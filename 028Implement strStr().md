# 28. Implement strStr()

Implement strStr().

Returns the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.


```javascript
/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */
var strStr = function(haystack, needle) {
  if(needle.length > haystack.length) return -1
  for(var i = 0, len = haystack.length - needle.length + 1; i < len; i++) {
    var j = 0
    for(; j < needle.length; j++) {
      if(haystack[i + j] !== needle[j]) {
        break
      }
    }
    if(j === needle.length) return i
  }
  return -1
};
```
