# 205. Isomorphic Strings

Given two strings **s** and **t**, determine if they are isomorphic.

Two strings are isomorphic if the characters in **s** can be replaced to get **t**.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character but a character may map to itself.

For example,  
Given `"egg"`, `"add"`, return true.

Given `"foo"`, `"bar"`, return false.

Given `"paper"`, `"title"`, return true.

Note:
You may assume both **s** and **t** have the same length.

```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isIsomorphic = function(s, t) {
  var sMap = {}
  var tMap = {}
  for (var i = 0, len = s.length; i < len; i++) {
    // 要么该字母没出现过(undefine)，要么出现的位置相同
    if (sMap[s[i]] !== tMap[t[i]]) return false
    sMap[s[i]] = i
    tMap[t[i]] = i
  }
  return true
};
```
