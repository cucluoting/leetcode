# 66. Plus One

Given a non-negative integer represented as a **non-empty** array of digits, plus one to the integer.

You may assume the integer do not contain any leading zero, except the number 0 itself.

The digits are stored such that the most significant digit is at the head of the list.

主要是需要考虑进位问题，包括数组最高位进位问题

```javascript
/**
 * @param {number[]} digits
 * @return {number[]}
 */
var plusOne = function(digits) {
  for(var i = digits.length - 1; i >= 0; i--) {
    var tempNumber = digits[i] + 1
    digits[i] = tempNumber % 10
    if(tempNumber < 10) return digits
  }
  digits.unshift(1)
  return digits
};
```
