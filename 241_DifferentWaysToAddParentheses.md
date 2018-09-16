# 241. Different Ways to Add Parentheses

Given a string of numbers and operators, return all possible results from computing all the different possible ways to group numbers and operators. The valid operators are +, - and *.

**Example 1:**
```
Input: "2-1-1"
Output: [0, 2]
Explanation: 
((2-1)-1) = 0 
(2-(1-1)) = 2
```
**Example 2:**
```
Input: "2*3-4*5"
Output: [-34, -14, -10, -10, 10]
Explanation: 
(2*(3-(4*5))) = -34 
((2*3)-(4*5)) = -14 
((2*(3-4))*5) = -10 
(2*((3-4)*5)) = -10 
(((2*3)-4)*5) = 10
```

```javascript
/**
 * @param {string} input
 * @return {number[]}
 */
var diffWaysToCompute = function(input) {
  const result = [];
  for (var i = 0; i < input.length; i++) {
    if ('+-*'.indexOf(input[i]) !== -1) {
      const left = diffWaysToCompute(input.substr(0, i));
      const right = diffWaysToCompute(input.substr(i + 1));
      for (var j = 0; j < left.length; j++) {
        for (var k = 0; k < right.length; k++) {
          let tempVal = 0
          if (input[i] === '+') {
            tempVal = left[j] + right[k]
          } else if (input[i] === '-') {
            tempVal = left[j] - right[k]
          } else {
            tempVal = left[j] * right[k]
          }
          result.push(tempVal)
        }
      }
    }
  }
  if (result.length === 0) result.push(+input)
  return result
};
```
