# 633. Sum of Square Numbers
Given a non-negative integer c, your task is to decide whether there're two integers a and b such that a2 + b2 = c.

**Example 1:**
```
Input: 5
Output: True
Explanation: 1 * 1 + 2 * 2 = 5
```

**Example 2:**
```
Input: 3
Output: False
```

```javascript
/**
 * @param {number} c
 * @return {boolean}
 */
var judgeSquareSum = function(c) {
  let left = 0
  let right = Math.floor(Math.sqrt(c))
  let sum
  while (left <= right) {
    sum = left * left + right * right
    if (sum === c) {
      return true
    } else if (sum < c) {
      left++
    } else {
      right--
    }
  }
  return false
}

```
