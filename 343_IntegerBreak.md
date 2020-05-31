# 343. Integer Break

Given a positive integer n, break it into the sum of at least two positive integers and maximize the product of those integers. Return the maximum product you can get.

**Example 1:**
```
Input: 2
Output: 1
Explanation: 2 = 1 + 1, 1 × 1 = 1.
```

**Example 2:**
```
Input: 10
Output: 36
Explanation: 10 = 3 + 3 + 4, 3 × 3 × 4 = 36.
```

**Note:** You may assume that n is not less than 2 and not larger than 58.

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var integerBreak = function(n) {
  let p = n % 3
  let q = Math.floor(n / 3)
  let r = p + (2 * p + 1) % 5
  return n <= 3 ? n - 1 : Math.pow(3, q - (p & 1)) * r
};
```
