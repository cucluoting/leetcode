# 17. Letter Combinations of a Phone Number

Given a digit string, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below.

```
Input:Digit string "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```

我的解法
```javascript
/**
 * @param {string} digits
 * @return {string[]}
 */
var letterCombinations = function(digits) {
  if(digits.length === 0) return []
  return getLetters([], digits.split(''))
};

var getLetters = function(arr, digits) {
  if(digits.length === 0) return arr

  var LETTER_MAP = {
    2: 'abc',
    3: 'def',
    4: 'ghi',
    5: 'jkl',
    6: 'mno',
    7: 'pqrs',
    8: 'tuv',
    9: 'wxyz'
  }
  var newArr = []
  var digit = digits.splice(0, 1)
  var letter = LETTER_MAP[digit]
  for(var i = 0, len = letter.length; i < len; i++) {
    if(arr.length > 0) {
      for (var j = 0; j < arr.length; j++) {
        newArr.push(arr[j] + letter[i])
      }
    }else {
      newArr.push(letter[i])
    }
  }
  return getLetters(newArr, digits)
};
```

DFS解法

```javascript
/**
 * @param {string} digits
 * @return {string[]}
 */
var letterCombinations = function(digits) {
  if(digits.length === 0) return []
  var LETTER_MAP = {
    2: 'abc',
    3: 'def',
    4: 'ghi',
    5: 'jkl',
    6: 'mno',
    7: 'pqrs',
    8: 'tuv',
    9: 'wxyz'
  }
  var result = []
  dfs(digits, LETTER_MAP, 0, result, '')
  return result
};

var dfs = function(digits, LETTER_MAP, level, result, temp) {
  if(level === digits.length) {
    result.push(temp)
    return result
  }

  var letters = LETTER_MAP[digits[level]]
  // 遍历该级所有字符
  for(var i = 0, len = letters.length; i < len; i++) {
    temp += letters[i]
    // 在该级该字符的基础上遍历下一级字符的所有可能
    dfs(digits, LETTER_MAP, level + 1, result, temp)
    // 把该级字符剔除，使得下一次循环中加入别的同级字符
    temp = temp.substring(0, temp.length - 1)
  }
};
```
