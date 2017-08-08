# 73. Set Matrix Zeroes

Given a m x n matrix, if an element is 0, set its entire row and column to 0. Do it in place.

**Follow up:**  
Did you use extra space?  
A straight forward solution using O(mn) space is probably a bad idea.  
A simple improvement uses O(m + n) space, but still not the best solution.  
Could you devise a constant space solution?

```javascript
/**
 * @param {number[][]} matrix
 * @return {void} Do not return anything, modify matrix in-place instead.
 */
var setZeroes = function(matrix) {
  var m = matrix[0].length
  var n = matrix.length
  var rows = []
  var cols = []
  for (var i = 0; i < n; i++) {
    for (var j = 0; j < m; j++) {
      if (matrix[i][j] === 0) {
        rows.push(i)
        cols.push(j)
      }
    }
  }
  for (var i = 0; i < rows.length; i++) {
    var row = rows[i]
    for (var j = 0; j < m; j++) {
      matrix[row][j] = 0
    }
  }
  for (var i = 0; i < cols.length; i++) {
    var col = cols[i]
    for (var j = 0; j < n; j++) {
      matrix[j][col] = 0
    }
  }
};
```
