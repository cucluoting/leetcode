# 342. Power of Four

Given an integer (signed 32 bits), write a function to check whether it is a power of 4.

**Example 1:**
```
Input: 16
Output: true
```
**Example 2:**
```
Input: 5
Output: false
```
**Follow up:** Could you solve it without loops/recursion?

```javascript
/**
 * @param {number} num
 * @return {boolean}
 */
var isPowerOfFour = function(num) {
  return (Math.log10(num) / Math.log10(4)) % 1 === 0
};
```
