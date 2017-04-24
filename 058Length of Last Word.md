# 58. Length of Last Word

Given a string s consists of upper/lower-case alphabets and empty space characters `' '`, return the length of last word in the string.

If the last word does not exist, return 0.

**Note:** A word is defined as a character sequence consists of non-space characters only.

For example,   
Given s = `"Hello World"`,  
return `5`.

...可能我没救了

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLastWord = function(s) {
  var tempArr = s.trim().split(' ')
  return tempArr[tempArr.length - 1].length
};
```

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLastWord = function(s) {
  var lastIndex = s.length - 1
  while(lastIndex >= 0 && s[lastIndex] === ' ') {
    lastIndex--
  }
  var firstIndex = lastIndex
  while(firstIndex >= 0 && s[firstIndex] !== ' ') {
    firstIndex--
  }
  
  return lastIndex - firstIndex
};
```
