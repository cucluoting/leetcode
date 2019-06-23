# 326. Power of Three

Given an integer, write a function to determine if it is a power of three.

**Example 1:**
```
Input: 27
Output: true
```
**Example 2:**
```
Input: 0
Output: false
```
**Example 3:**
```
Input: 9
Output: true
```
**Example 4:**
```
Input: 45
Output: false
```

**Follow up:**
Could you do it without using any loop / recursion?

换底公式：log<sub>a</sub>b = log<sub>c</sub>b / log<sub>c</sub>a

```javascript
/**
 * @param {number} n
 * @return {boolean}
 */
var isPowerOfThree = function(n) {
  return (Math.log10(n) / Math.log10(3)) % 1 === 0
};
```
