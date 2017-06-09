# 171. Excel Sheet Column Number

Related to question [Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/#/description)

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:
```
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
```

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var titleToNumber = function(s) {
  var number = 0
  for (var i = 0, len = s.length; i < len; i++) {
    number = number * 26 + (s[i].charCodeAt() - 64)
  }
  return number
};
```
