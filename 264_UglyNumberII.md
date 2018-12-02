# 264. Ugly Number II

Write a program to find the n-th ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. 

**Example:**
```
Input: n = 10
Output: 12
Explanation: 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 is the sequence of the first 10 ugly numbers.
```

**Note:**  

1. 1 is typically treated as an ugly number.
2. n does not exceed 1690.

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var nthUglyNumber = function(n) {
  const tempArr = [1]
  let i2 = 0
  let i3 = 0
  let i5 = 0 
  while (tempArr.length < n) {
    const num2 = tempArr[i2] * 2
    const num3 = tempArr[i3] * 3
    const num5 = tempArr[i5] * 5
    const minNum = Math.min(num5, num3, num2)
    if (minNum === num2) i2++
    if (minNum === num3) i3++
    if (minNum === num5) i5++
    tempArr.push(minNum)
  }
  return tempArr[n - 1]
};
```
