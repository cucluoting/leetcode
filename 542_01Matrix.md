# 542. 01 Matrix

Given a matrix consists of 0 and 1, find the distance of the nearest 0 for each cell.

The distance between two adjacent cells is 1.

 
**Example 1:**
```
Input:
[[0,0,0],
 [0,1,0],
 [0,0,0]]

Output:
[[0,0,0],
 [0,1,0],
 [0,0,0]]
```

**Example 2:**
```
Input:
[[0,0,0],
 [0,1,0],
 [1,1,1]]

Output:
[[0,0,0],
 [0,1,0],
 [1,2,1]]
```

**Note:**

1. The number of elements of the given matrix will not exceed 10,000.
2. There are at least one 0 in the given matrix.
3. The cells are adjacent in only four directions: up, down, left and right.

```javascript
/**
 * @param {number[][]} matrix
 * @return {number[][]}
 */
var updateMatrix = function(matrix) {
  const rows = matrix.length
  const cols = matrix[0].length
  const dist = []
  for (let row = 0; row < rows; row++) {
    dist[row] = []
    for (let col = 0; col < cols; col++) {
      dist[row][col] = (matrix[row][col] === 0 ? 0 : Number.MAX_VALUE)
    }
  }
  for (let row = 0; row < rows; row++) {
    for (let col = 0; col < cols; col++) {
      if (row > 0) {
        dist[row][col] = Math.min(dist[row][col], dist[row - 1][col] + 1)
      }
      if (col > 0) {
        dist[row][col] = Math.min(dist[row][col], dist[row][col - 1] + 1)
      }
    }
  }
  for (let row = rows - 1; row >= 0; row--) {
    for (let col = cols - 1; col >= 0; col--) {
      if (row < rows - 1) {
        dist[row][col] = Math.min(dist[row][col], dist[row + 1][col] + 1)
      }
      if (col < cols - 1) {
        dist[row][col] = Math.min(dist[row][col], dist[row][col + 1] + 1)
      }
    }
  }
  return dist
};

```
