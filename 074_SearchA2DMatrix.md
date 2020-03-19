# 74. Search a 2D Matrix

Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:

- Integers in each row are sorted from left to right.  
- The first integer of each row is greater than the last integer of the previous row.  
For example,  

Consider the following matrix:
```
[
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
```

**Given** target = `3`, return `true`.

```javascript
/**
 * @param {number[][]} matrix
 * @param {number} target
 * @return {boolean}
 */
var searchMatrix = function(matrix, target) {
  if (matrix.length === 0 || matrix[0].length === 0) return false
  var rows = matrix.length
  var cols = matrix[0].length
  var row = rows - 1
  var col = 0
  while (row >= 0 && col <= cols - 1) {
    if (matrix[row][col] < target) {
      col++
    } else if (matrix[row][col] > target) {
      row--
    } else {
      return true
    }
  }
  return false
};
```

二分法：
```javascript
/**
 * @param {number[][]} matrix
 * @param {number} target
 * @return {boolean}
 */
var searchMatrix = function(matrix, target) {
  let m = matrix.length
  if (m === 0) return false
  let n = matrix[0].length

  let left = 0 
  let right = m * n - 1
  while (left <= right) {    
    const index = Math.floor((left + right) / 2)
    const num = matrix[Math.floor(index / n)][index % n]
    if (num === target) {
      return true
    } else if (num < target) {
      left = index + 1
    } else {
      right = index - 1
    }
  }
  
  return false
};
```
