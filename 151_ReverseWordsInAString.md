# 151. Reverse Words in a String

Given an input string, reverse the string word by word.

For example,  
Given s = "`the sky is blue`",  
return "`blue is sky the`".

```javascript
/**
 * @param {string} str
 * @returns {string}
 */
var reverseWords = function(str) {
  return str.trim().replace(/\s+/g, ' ').split(' ').reverse().join(' ')
};
```
