# 67. Add Binary

Given two binary strings, return their sum (also a binary string).

For example,  
a = `"11"`  
b = `"1"`  
Return `"100"`.  

```javascript
/**
 * @param {string} a
 * @param {string} b
 * @return {string}
 */
var addBinary = function(a, b) {
  if(a.length === 0) return b
  if(b.length === 0) return a
  var result = '',
      aLength = a.length,
      bLength = b.length,
      overFlow = 0,
      i = 1
  while(a[aLength - i] || b[bLength - i]) {
    var tempA = a[aLength - i] ? a[aLength - i] * 1 : 0,
        tempB = b[bLength - i] ? b[bLength - i] * 1 : 0,
        tempR = tempA + tempB + overFlow
    if(tempR > 1) {
      overFlow = 1
      result = (tempR - 2) + result
    }else {
      overFlow = 0
      result = tempR + result
    }
    i++
  }
  if(overFlow > 0) result = overFlow + result

  return result
};
```
