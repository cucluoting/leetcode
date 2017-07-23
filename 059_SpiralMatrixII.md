# 59. Spiral Matrix II

Given an integer n, generate a square matrix filled with elements from 1 to n2 in spiral order.

For example,  
Given n = 3,

You should return the following matrix:
```
[
 [ 1, 2, 3 ],
 [ 8, 9, 4 ],
 [ 7, 6, 5 ]
]
```

--> [Spiral Matrix](https://github.com/cucluoting/leetcode/blob/master/054_SpiralMatrix.md)

```javascript
/**
 * @param {number} n
 * @return {number[][]}
 */
var generateMatrix = function(n) {
  var result = []
  for (var i = 0; i < n; i++) {
    result[i] = []
  }
  var number = 1
  var level = Math.floor(n / 2)
  for (var i = 0; i < level; i++) {
    for (var j = i; j < n - 1 - i; j++) {
      result[i][j] = number++
    }
    for (var j = i; j < n - 1 - i; j++) {
      result[j][n - 1 - i] = number++
    }
    for (var j = n - 1 - i; j > i; j--) {
      result[n - 1 - i][j] = number++
    }
    for (var j = n - 1 - i; j > i; j--) {
      result[j][i] = number++
    }
  }
  if (n % 2 !== 0) {
    for (var i = level; i < n - level; i++) {
      result[level][i] = number++
    }
  }
  return result
};
```
