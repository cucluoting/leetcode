# 14. Longest Common Prefix

Write a function to find the longest common prefix string amongst an array of strings.

基本思路是先找出最短的，从短到长提取前缀，对数组的每一个字符串进行匹配。

如果当前前缀遇到不匹配的字符串，则返回前一个前缀。

```javascript
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
  var tempStr = strs[0] || '',
      prefix = ''
  for(var i = 0, len = strs.length; i < len; i++) {
    if(strs[i].length < tempStr.length) {
      tempStr = strs[i]
    }
  }
  for(var i = 0, len = tempStr.length; i < len; i++) {
    prefix = tempStr.slice(0, i + 1)
    for(var j = 0, strsLen = strs.length; j < strsLen; j++) {
      if(strs[j].slice(0, i + 1) !== prefix) {
        return prefix.slice(0, i)
      }
    }
  }
  return prefix
};
```

其实不用找出最短的是哪个字符串，只需要找到最短的字符串长度就好了

升级写法（用了array.reduce()和array.every()的写法

```javascript
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
  var prefix = '',
      tempStr = ''
  if(strs.length <= 0) return ''
  var minStrLen = strs.reduce(function(a, b) {
    return b.length < a ? b.length : a
  }, strs[0].length)
  for(var i = 0; i < minStrLen; i++) {
    tempStr = strs[0][i]
    var commonYN = strs.every(function(item) {
      return item[i] == tempStr
    })
    if(!commonYN) break
    prefix += tempStr
  }
  return prefix
};
```
