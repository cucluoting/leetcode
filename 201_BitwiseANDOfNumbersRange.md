# 201. Bitwise AND of Numbers Range

Given a range [m, n] where 0 <= m <= n <= 2147483647, return the bitwise AND of all numbers in this range, inclusive.

For example, given the range [5, 7], you should return 4.


**解题思路**：找出m和n左边的共同首部。（如001，010，011结果是0。101，110，111结果是100

```javascript
/**
 * @param {number} m
 * @param {number} n
 * @return {number}
 */
var rangeBitwiseAnd = function(m, n) {
  if (m === 0) return 0
  var d = (2**31) - 1
  while((m & d) !== (n & d)) {
    d <<= 1
  }
  return m & d
};
```
