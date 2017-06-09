# 8. String to Integer (atoi)

Implement atoi to convert a string to an integer.

**Hint:** Carefully consider all possible input cases. If you want a challenge, please do not see below and ask yourself what are the possible input cases.

**Notes:** It is intended for this problem to be specified vaguely (ie, no given input specs). You are responsible to gather all the input requirements up front.

```javascript
/**
 * @param {string} str
 * @return {number}
 */
var myAtoi = function(str) {
  var number = 0
  var numberArr = []
  var sign = 1

  str = str.trim()
  if(str.length === 0) return number
  
  if(str[0] === '-') {
    sign = -1
    str = str.substring(1)
  }else if(str[0] === '+') {
    str = str.substring(1)
  }
  
  for (var i = 0; i < str.length; i++) {
    if(str[i].charCodeAt() >= 48 && str[i].charCodeAt() <= 57) {
      numberArr.push(str[i])
    }else {
      break
    }
  }

  var INT_MIN = - (2**31)
  var INT_MAX = (2**31) - 1
  for (var i = 0; i < numberArr.length; i++) {
    var tempNum = numberArr[i] * 1;
    if(sign === 1 && (INT_MAX - tempNum) / 10 < number) {
      number = INT_MAX
      break
    }else if(sign === -1 && (- INT_MIN - tempNum) / 10 < number) {
      number = Math.abs(INT_MIN)
      break
    }else {
      number = number * 10 + tempNum
    }
  }
  return number * sign
};
```
