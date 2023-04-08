# 54. Spiral Matrix

Given a matrix of m x n elements (m rows, n columns), return all elements of the matrix in spiral order.

For example,
Given the following matrix:

```
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
```

You should return `[1,2,3,6,9,8,7,4,5]`.

```javascript
/**
 * @param {number[][]} matrix
 * @return {number[]}
 */
var spiralOrder = function(matrix) {
  var result = []
  if (matrix.length === 0 || matrix[0].length === 0) return result
  var minLen = Math.min(matrix[0].length, matrix.length)
  var level = Math.floor(minLen / 2)
  for (var i = 0; i < level; i++) {
    for (var j = i; j < matrix[0].length - 1 - i; j++) {
      result.push(matrix[i][j])
    }
    for (var j = i; j < matrix.length - 1 - i; j++) {
      result.push(matrix[j][matrix[0].length - 1 - i])
    }
    for (var j = matrix[0].length - 1 - i; j > i; j--) {
      result.push(matrix[matrix.length - 1 - i][j])
    }
    for (var j = matrix.length - 1 - i; j > i; j--) {
      result.push(matrix[j][i])
    }
  }
  if (minLen % 2 !== 0) {
    if (matrix[0].length < matrix.length) {
      for (var i = level; i < matrix.length - level; i++) {
        result.push(matrix[i][level])
      }
    } else {
      for (var i = level; i < matrix[0].length - level; i++) {
        result.push(matrix[level][i])
      }
    }
  }
  return result
};
```

直接修改矩阵法：
```javascript
var spiralOrder = function(matrix) {
  const result = [];
  while(matrix.length) {
    // 从左到右推入行
    result.push(...matrix.shift());
    // 从上到下推入最后一列
    for (let i = 0; i < matrix.length; i++) {
      const value = matrix[i].pop();
      if (value) {
        result.push(value);
      }
      // 旋转行元素
      matrix[i].reverse();
    }
    // 旋转列元素
    matrix.reverse();
  }
  return result;
}
```
