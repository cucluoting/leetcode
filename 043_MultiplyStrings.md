# 43. Multiply Strings

Given two non-negative integers `num1` and `num2` represented as strings, return the product of `num1` and `num2`.

**Note:**

1. The length of both `num1` and `num2` is < 110.  
2. Both `num1` and `num2` contains only digits `0-9`.  
3. Both `num1` and `num2` does not contain any leading zero.  
4. You **must not use any built-in BigInteger library** or **convert the inputs to integer** directly.  

```javascript
/**
 * @param {string} num1
 * @param {string} num2
 * @return {string}
 */
var multiply = function(num1, num2) {
  if (num1.length === 0 || num2.length === 0) return ''
  if (num1[0] === '0' || num2[0] === '0') return '0'
  var result = ''
  var tempArr = []
  for (var i = num1.length - 1; i >= 0; i--) {
    for (var j = num2.length - 1; j >= 0; j--) {
      var tempSum = (num1[i] - '0') * (num2[j] - '0')
      tempArr[i + j + 1] = tempArr[i + j + 1] ? tempArr[i + j + 1] + tempSum : tempSum
    }
  }
  var carryBit = 0
  for (var i = num1.length + num2.length - 1; i > 0; i--) {
    tempArr[i] += carryBit
    carryBit = Math.floor(tempArr[i] / 10)
    result = tempArr[i] % 10 + '' + result
  }
  if (carryBit > 0) result = carryBit + result
  return result
};
```
