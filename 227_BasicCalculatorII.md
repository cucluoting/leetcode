# 227. Basic Calculator II

Implement a basic calculator to evaluate a simple expression string.

The expression string contains only **non-negative** integers, `+`, `-`, `*`, `/` operators and empty spaces . The integer division should truncate toward zero.

**Example 1:**
```
Input: "3+2*2"
Output: 7
```

**Example 2:**
```
Input: " 3/2 "
Output: 1
```

**Example 3:**
```
Input: " 3+5 / 2 "
Output: 5
```

**Note:**

- You may assume that the given expression is always valid.
- **Do not** use the `eval` built-in library function.

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var calculate = function(s) {
  s = s.replace(/ /g, '')
  let result = 0
  let tempResult = 0
  let num = 0
  let op = '+'
  for (let i = 0, len = s.length; i < len; i++) {
    if ('+-*/'.indexOf(s[i]) === -1) {
      num = num * 10 + s[i] * 1
    } 
    if ('+-*/'.indexOf(s[i]) > -1 || i === len - 1) {
      switch (op) {
        case '+': tempResult += num;break;
        case '-': tempResult -= num;break;
        case '*': tempResult *= num;break;
        case '/': tempResult = parseInt(tempResult / num);break;
      }
      if ('+-'.indexOf(s[i]) > -1 || i === len - 1) {
        result += tempResult
        tempResult = 0
      }
      num = 0
      op = s[i]
    }
  }
  return result
};
```
