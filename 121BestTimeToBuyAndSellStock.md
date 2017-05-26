# 121. Best Time to Buy and Sell Stock

Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

**Example 1:**

```
Input: [7, 1, 5, 3, 6, 4]
Output: 5

max. difference = 6-1 = 5 (not 7-1 = 6, as selling price needs to be larger than buying price)
```

**Example 2:**

```
Input: [7, 6, 4, 3, 1]
Output: 0

In this case, no transaction is done, i.e. max profit = 0.
```

解法一：（比较单纯...
```javascript
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
  var profit = 0
  for(var i = 0, len = prices.length; i < len - 1; i++) {
    var tempMaxProfit = 0
    for(var j = i + 1; j < len; j++) {
      tempMaxProfit = Math.max(prices[j] - prices[i], tempMaxProfit)
    }
    profit = Math.max(tempMaxProfit, profit)
  }
  return profit
};
```

解法二：（其实就是要找出最小的买入价格，顺便一直更新利润
```javascript
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
  if(prices.length < 2) return 0
  var profit = 0
  var minPrice = prices[0]
  for(var i = 1, len = prices.length; i < len; i++) {
    profit = Math.max(prices[i] - minPrice, profit)
    minPrice = Math.min(prices[i], minPrice)
  }
  return profit
};
```
