# 168. Excel Sheet Column Title

Given a positive integer, return its corresponding column title as appear in an Excel sheet.

For example:

```
    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 

```

🌟🌟🌟`fromCharCode()`——使用指定的Unicode值序列创建字符串

```javascript
/**
 * @param {number} n
 * @return {string}
 */
var convertToTitle = function(n) {
  var result = []
  while(n > 0) {
    if(n % 26 === 0) {
      result.unshift(String.fromCharCode(26 + 64))
      n = Math.floor(n / 26) - 1
    }else {
      result.unshift(String.fromCharCode((n % 26) + 64))
      n = Math.floor(n / 26)
    }
  }
  return result.join('')
};
```
