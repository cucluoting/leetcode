# 417. Pacific Atlantic Water Flow
There is an m x n rectangular island that borders both the Pacific Ocean and Atlantic Ocean. The Pacific Ocean touches the island's left and top edges, and the Atlantic Ocean touches the island's right and bottom edges.

The island is partitioned into a grid of square cells. You are given an m x n integer matrix heights where heights[r][c] represents the height above sea level of the cell at coordinate (r, c).

The island receives a lot of rain, and the rain water can flow to neighboring cells directly north, south, east, and west if the neighboring cell's height is less than or equal to the current cell's height. Water can flow from any cell adjacent to an ocean into the ocean.

Return a 2D list of grid coordinates result where result[i] = [ri, ci] denotes that rain water can flow from cell (ri, ci) to both the Pacific and Atlantic oceans.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/06/08/waterflow-grid.jpg)
```
Input: heights = [[1,2,2,3,5],[3,2,3,4,4],[2,4,5,3,1],[6,7,1,4,5],[5,1,1,2,4]]
Output: [[0,4],[1,3],[1,4],[2,2],[3,0],[3,1],[4,0]]
```

**Example 2:**
```
Input: heights = [[2,1],[1,2]]
Output: [[0,0],[0,1],[1,0],[1,1]]
```

**Constraints:**

- m == heights.length
- n == heights[r].length
- 1 <= m, n <= 200
- 0 <= heights[r][c] <= 105

```javascript
/**
 * @param {number[][]} heights
 * @return {number[][]}
 */
var pacificAtlantic = function (heights) {
  if (heights.length === 0) return []
  const rows = heights.length
  const columns = heights[0].length
  const pacific = []
  const atlantic = []
  for (let i = 0; i < rows; i++) {
    pacific[i] = []
    atlantic[i] = []
    for (let j = 0; j < columns; j++) {
      pacific[i][j] = false
      atlantic[i][j] = false
    }
  }
  for (let y = 0; y < columns; y++) {
    // top
    dfs(heights, 0, y, 0, pacific)
    // bottom
    dfs(heights, rows - 1, y, 0, atlantic)
  }
  for (let x = 0; x < rows; x++) {
    // left
    dfs(heights, x, 0, 0, pacific)
    // right
    dfs(heights, x, columns - 1, 0, atlantic)
  }
  const result = []
  for (let i = 0; i < rows; i++) {
    for (let j = 0; j < columns; j++) {
      if (pacific[i][j] && atlantic[i][j]) {
        result.push([i, j])
      }
    }
  }
  return result
};

var dfs = function (heights, x, y, h, matrix) {
  if (x < 0 || y < 0 || y === heights[0].length || x === heights.length) {
    return
  }
  if (matrix[x][y] || heights[x][y] < h) {
    return
  }
  matrix[x][y] = true
  dfs(heights, x + 1, y, heights[x][y], matrix)
  dfs(heights, x - 1, y, heights[x][y], matrix)
  dfs(heights, x, y + 1, heights[x][y], matrix)
  dfs(heights, x, y - 1, heights[x][y], matrix)
}
```
