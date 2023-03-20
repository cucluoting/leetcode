# 123. Best Time to Buy and Sell Stock III

You are given an array prices where prices[i] is the price of a given stock on the ith day.

Find the maximum profit you can achieve. You may complete at most two transactions.

**Note:** You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).

**Example 1:**
```
Input: prices = [3,3,5,0,0,3,1,4]
Output: 6
Explanation: Buy on day 4 (price = 0) and sell on day 6 (price = 3), profit = 3-0 = 3.
Then buy on day 7 (price = 1) and sell on day 8 (price = 4), profit = 4-1 = 3.
```
**Example 2:**
```
Input: prices = [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are engaging multiple transactions at the same time. You must sell before buying again.
```
**Example 3:**
```
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

**Constraints:**

- `1 <= prices.length <= 105`
- `0 <= prices[i] <= 105`

```javascript
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
  let buy1 = prices[0]
  let buy2 = prices[0]
  let sell1 = 0
  let sell2 = 0
  for (let i = 1; i < prices.length; i++) {
    // 求当前买入的最低价
    buy1 = Math.min(buy1, prices[i])
    // 求一次交易赚到的最大值
    sell1 = Math.max(sell1, prices[i] - buy1)
    // 结合上一次交易的收益求第二次买入的最低价
    buy2 = Math.min(buy2, prices[i] - sell1)
    // 当前卖出的最大收益
    sell2 = Math.max(sell2, prices[i] - buy2)
  }
  return sell2
};
```
