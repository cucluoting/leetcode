# 397. Integer Replacement
Given a positive integer n, you can apply one of the following operations:

1. If n is even, replace n with n / 2.
2. If n is odd, replace n with either n + 1 or n - 1.
Return the minimum number of operations needed for n to become 1.

**Example 1:**
```
Input: n = 8
Output: 3
Explanation: 8 -> 4 -> 2 -> 1
```
**Example 2:**
```
Input: n = 7
Output: 4
Explanation: 7 -> 8 -> 4 -> 2 -> 1
or 7 -> 6 -> 3 -> 2 -> 1
```
**Example 3:**
```
Input: n = 4
Output: 2
```

**Constraints:**

- 1 <= n <= 231 - 1


```javascript
/**
 * @param {number} n
 * @return {number}
 */
var integerReplacement = function (n) {
  if (Math.pow(2, 31) - 1 === n) {
    return 32
  }
  let result = 0
  while (n !== 1) {
    // 偶数右移
    if ((n & 1) === 0) {
      n >>= 1
    } else {
      // 奇数01或3(-1), 11(+1), 使1的数目越少越好
      n += (((n & 2) === 0) || n === 3) ? -1 : 1
    }
    result += 1
  }
  return result
};
```
