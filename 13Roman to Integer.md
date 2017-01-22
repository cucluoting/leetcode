# 13. Roman to Integer

Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.


```javascript
/**
 * @param {string} s
 * @return {number}
 */
var romanToInt = function(s) {
  var map = {
    'I': 1,
    'V': 5,
    'X': 10,
    'L': 50,
    'C': 100,
    'D': 500,
    'M': 1000,
  },
  result = 0
  for(var i = 0, len = s.length; i < len; i++) {
    var current = map[s[i]]
    if(i > 0) {
      var prev = map[s[i - 1]]
      result = prev < current ? result - 2 * prev + current : result + current
    }else {
      result = result + current
    }
  }
  return result
};
```
