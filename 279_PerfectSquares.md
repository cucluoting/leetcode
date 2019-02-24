# 279. Perfect Squares
Given a positive integer n, find the least number of perfect square numbers (for example, `1, 4, 9, 16, ...`) which sum to n.

**Example 1:**
```
Input: n = 12
Output: 3 
Explanation: 12 = 4 + 4 + 4.
```
**Example 2:**
```
Input: n = 13
Output: 2
Explanation: 13 = 4 + 9.
```

- [四平方和定理](https://zh.wikipedia.org/wiki/%E5%9B%9B%E5%B9%B3%E6%96%B9%E5%92%8C%E5%AE%9A%E7%90%86)

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var numSquares = function(n) {
  while (n % 4 === 0) n = n / 4
  if (n % 8 === 7) return 4
  for (let i = 0; i * i <= n; i++) {
    const j = Math.round(Math.sqrt(n - i * i))
    if (i * i + j * j === n) return !!i + !!j
  }
  return 3
};
```
