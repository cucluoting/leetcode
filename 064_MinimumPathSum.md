# 64. Minimum Path Sum

Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

**Note:** You can only move either down or right at any point in time.

```javascript
/**
 * @param {number[][]} grid
 * @return {number}
 */
var minPathSum = function(grid) {
  var m = grid.length
  var n = grid[0].length

  var tempSumArr = []
  tempSumArr[0] = grid[0][0]
  for (var i = 1; i < n; i++) {
    tempSumArr[i] = grid[0][i] + tempSumArr[i - 1]
  }

  for (var i = 1; i < m; i++) {
    tempSumArr[0] += grid[i][0]
    for (var j = 1; j < n; j++) {
      tempSumArr[j] = Math.min(tempSumArr[j - 1], tempSumArr[j]) + grid[i][j]
    }
  }
  return tempSumArr[n - 1]
};
```

update:
```javascript
/**
 * @param {number[][]} grid
 * @return {number}
 */
var minPathSum = function(grid) {
  const rows = grid.length
  const cols = grid[0].length
  const dist = new Array(grid[0].length).fill(0)
  for (let row = rows - 1; row >= 0; row--) {
    for (let col = cols - 1; col >= 0; col--) {
      if (row === rows - 1) {
        dist[col] = grid[row][col] + (col === cols - 1 ? 0 : dist[col + 1])
      } else {
        dist[col] = grid[row][col] + (col === cols - 1 ? dist[col] : Math.min(dist[col], dist[col + 1]))
      }
    }
  }
  return dist[0]
};
```
