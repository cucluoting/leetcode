# 29. Divide Two Integers

Divide two integers without using multiplication, division and mod operator.

If it is overflow, return MAX_INT.

⬇️位运算

```javascript
/**
 * @param {number} dividend
 * @param {number} divisor
 * @return {number}
 */
var divide = function(dividend, divisor) {
  var isNeg = (dividend ^ divisor) >>> 31 === 1
  var INT_MIN = - (2**31)
  var INT_MAX = (2**31) - 1
  if(divisor === 0) {
    return isNeg ? INT_MIN : INT_MAX
  }
  var result = 0
  if(dividend === INT_MIN) {
    dividend += Math.abs(divisor)
    result++

    if(divisor === -1) return INT_MAX
  }
  if(divisor === INT_MIN) {
    return result
  }
  dividend = Math.abs(dividend)
  divisor = Math.abs(divisor)

  var digit = 0
  while(divisor <= (dividend >> 1)) {
    divisor <<= 1
    digit++
  }
  while(digit >= 0) {
    if(dividend >= divisor) {
      result += 1<<digit
      dividend -= divisor
    }
    digit--
    divisor >>= 1
  }
  
  return isNeg ? -result : result
};
```
