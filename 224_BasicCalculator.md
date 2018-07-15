# 224. Basic Calculator

Implement a basic calculator to evaluate a simple expression string.

The expression string may contain open `(` and closing parentheses `)`, the plus `+` or minus sign `-`, non-negative integers and empty spaces ` `.

**Example 1:**
```
Input: "1 + 1"
Output: 2
```

**Example 2:**
```
Input: " 2-1 + 2 "
Output: 3
```

**Example 3:**
```
Input: "(1+(4+5+2)-3)+(6+8)"
Output: 23
```

**Note:**
- You may assume that the given expression is always valid.
- **Do not** use the `eval` built-in library function.

栈
```javascript
/**
 * @param {string} s
 * @return {number}
 */
var calculate = function(s) {
  s = s.replace(/ /g, '')
  let num = 0
  let result = 0
  let sign = 1
  let stack = []
  for (let i = 0, len = s.length; i < len; i++) {
    if ('+-()'.indexOf(s[i]) === -1) {
      num = num * 10 + s[i] * 1
    } else if (s[i] === '(') {
      stack.push(result)
      stack.push(sign)
      result = 0
      sign = 1
    } else if (s[i] === ')') {
      result += sign * num
      num = 0
      result *= stack.pop()
      result += stack.pop()
    }
    if (s[i] === '+' || s[i] === '-' || i === len - 1) {
      result += sign * num
      num = 0
      sign = s[i] === '-' ? -1 : 1
    }
  }
  return result
};
```

递归
```javascript
/**
 * @param {string} s
 * @return {number}
 */
var calculate = function(s) {
  s = s.replace(/ /g, '')
  let num = 0
  let result = 0
  let sign = 1
  for (let i = 0, len = s.length; i < len; i++) {
    if ('+-()'.indexOf(s[i]) === -1) {
      num = num * 10 + s[i] * 1
    } else if (s[i] === '(') {
      let j = i + 1
      let cnt = 0
      for (; i < len; i++) {
        if (s[i] === '(') ++cnt
        if (s[i] === ')') --cnt
        if (cnt === 0) break
      }
      num = calculate(s.substring(j, i))
    } 
    if (s[i] === '+' || s[i] === '-' || i === len - 1) {
      result += sign * num
      num = 0
      sign = s[i] === '-' ? -1 : 1
    }
  }
  return result
};
```
