# 150. Evaluate Reverse Polish Notation

Evaluate the value of an arithmetic expression in [Reverse Polish Notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation).

Valid operators are `+, -, *, /`. Each operand may be an integer or another expression.

Some examples:
```
  ["2", "1", "+", "3", "*"] -> ((2 + 1) * 3) -> 9
  ["4", "13", "5", "/", "+"] -> (4 + (13 / 5)) -> 6
```

```javascript
/**
 * @param {string[]} tokens
 * @return {number}
 */
var evalRPN = function(tokens) {
  var numberArr = []
  for (var i = 0; i < tokens.length; i++) {
    if ('+-*/'.indexOf(tokens[i]) > -1) {
      var a = numberArr.pop()
      var b = numberArr.pop()
      switch (tokens[i]) {
        case '+': numberArr.push(b + a);break;
        case '-': numberArr.push(b - a);break;
        case '*': numberArr.push(b * a);break;
        case '/': numberArr.push(parseInt(b / a));break;
      }
    } else {
      numberArr.push(parseInt(tokens[i]))
    }
  }
  return numberArr.pop()
};
```
