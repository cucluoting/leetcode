# 20. Valid Parentheses

Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

The brackets must close in the correct order, `"()"` and `"()[]{}"` are all valid but `"(]"` and `"([)]"` are not.

**跟栈有关的题**

思路就是判断当前符号是开还是闭

如果为开的话判断后一个符号是开还是闭，如果为闭则它们应该索引值相等，如果为开就推入临时数组；

如果为闭的话，则他的索引值必定等于临时数组的最后一个元素的索引值。

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
  if(s.length % 2 !== 0) return false

  var openBrackets = '([{',
      closeBrackets = ')]}',
      openBracketsIndexArr = []

  for(var i = 0, len = s.length; i < len; i++) {
    var openBracketsIndex = openBrackets.indexOf(s[i])
    var closeBracketsIndex = closeBrackets.indexOf(s[i])

    if(openBracketsIndex > -1) {

      if(openBrackets.indexOf(s[i+1]) > -1) {
        openBracketsIndexArr.push(openBracketsIndex)
      }else if(
        closeBrackets.indexOf(s[i+1]) > -1 
        && openBracketsIndex === closeBrackets.indexOf(s[i+1])
      ) {
        i++
      }else {
        return false
      }

    }else if(closeBracketsIndex > -1) {

      if(openBracketsIndexArr.length === 0) {
        return false
      }else {
        var lastOpenIndexArrItem = openBracketsIndexArr[openBracketsIndexArr.length - 1]
        if(lastOpenIndexArrItem === closeBracketsIndex) {
          openBracketsIndexArr.pop()
        }else {
          return false
        }
      }

    }else {

      return false

    }
  }
  return true
};
```

上面的写法是我粗略形成的思路，太繁琐了，还有优化的空间，特别是两个字符串都要indexOf...就应该放到对象里，一个做key一个做value...

还有就是可以直接根据临时数组的长度是否为0来判断结果，不用急着返回false

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
  if(s.length % 2 !== 0) return false
  var tempArr = [],
      bracketsObj = {
        '(' : ')',
        '[' : ']',
        '{' : '}'
      }
  for(var i = 0, len = s.length; i < len; i++) {
    if(tempArr.length === 0) {
      tempArr.push(s[i])
    }else {
      if(s[i] === bracketsObj[tempArr[tempArr.length - 1]]) {
        tempArr.pop()
      }else {
        tempArr.push(s[i])
      }
    }
  }
  return !tempArr.length
};
```
