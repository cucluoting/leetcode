# 12. Integer to Roman

Given an integer, convert it to a roman numeral.

Input is guaranteed to be within the range from 1 to 3999.

```javascript
/**
 * @param {number} num
 * @return {string}
 */
var intToRoman = function(num) {
  // 把基本的和左减的情况列举出来，就可以直接按相加的处理了
  var romanArr = ['M', 'CM', 'D', 'CD', 'C', 'XC', 'L', 'XL', 'X', 'IX', 'V', 'IV', 'I']
  var map      = [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1]
  count = 0,
  tempNum = 0,
  result = ''
  for(var i = 0, len = map.length; i < len; i++) {
    if(num === 0) break
    while(num - map[i] >= 0) {
      num = num - map[i]
      result = result + romanArr[i]
    }
  }
  return result
};
```
