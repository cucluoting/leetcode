# 200. Number of Islands

Given a 2d grid map of `'1'`s (land) and `'0'`s (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

**Example 1:**

```
11110
11010
11000
00000
```
Answer: 1

**Example 2:**

```
11000
11000
00100
00011
```
Answer: 3

解题思路：需要对值为`'1'`的点做特殊处理，即凡是遇到值为`'1'`的点就给结果加一，
并排查相连的上下左右点的值，如果也为`'1'`的话说明是相连区域，将其设为其他值，
这样的话最后值为`'1'`的点的个数就对应着 islands 的个数。

```javascript
/**
 * @param {character[][]} grid
 * @return {number}
 */
var numIslands = function(grid) {
  if (grid.length === 0 || grid[0].length === 0) return 0
  var result = 0
  var n = grid.length
  var m = grid[0].length
  for (var row = 0; row < n; row++) {
    for (var col = 0; col < m; col++) {
      if (grid[row][col] === '1') {
        ++result
        helper(grid, row, col, n, m)
      }
    }
  }
  return result
};

var helper = function(grid, row, col, n, m) {
  if (row < 0 || col < 0 || row > n - 1 || col > m - 1 || grid[row][col] !== '1') return
  grid[row][col] = '#'
  helper(grid, row - 1, col, n, m)
  helper(grid, row, col + 1, n, m)
  helper(grid, row + 1, col, n, m)
  helper(grid, row, col - 1, n, m)
};
```
