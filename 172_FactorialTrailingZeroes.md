# 172. Factorial Trailing Zeroes

Given an integer n, return the number of trailing zeroes in n!.

Note: Your solution should be in logarithmic time complexity.

2乘以5就等于10，要求0的个数就是要求一对2和5的个数，而2的个数比5的多，每五个数就有一个5，同时要考虑5的n次方这种情况会不只一个5

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var trailingZeroes = function(n) {
  return n === 0 ? 0 : Math.floor(n / 5) + trailingZeroes(n / 5)
};
```
