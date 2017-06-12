# 22. Generate Parentheses

Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given n = 3, a solution set is:

```
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```

```javascript
/**
 * @param {number} n
 * @return {string[]}
 */
var generateParenthesis = function(n) {
  var result = []
  var item = ''
  if (n <= 0) return result
  helper(n, n, item, result)
  return result
};

var helper = function(l, r, item, result) {
  if(r < l) return
  if(r === 0 && l === 0) {
    result.push(item)
  }
  if(l > 0) helper(l - 1, r, item + '(', result)
  if(r > 0) helper(l, r - 1, item + ')', result)
};
```
