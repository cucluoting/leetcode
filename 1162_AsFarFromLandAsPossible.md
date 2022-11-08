# 1162. As Far from Land as Possible

Given an n x n grid containing only values 0 and 1, where 0 represents water and 1 represents land, find a water cell such that its distance to the nearest land cell is maximized, and return the distance. If no land or water exists in the grid, return -1.

The distance used in this problem is the Manhattan distance: the distance between two cells (x0, y0) and (x1, y1) is |x0 - x1| + |y0 - y1|.

**Example 1:**

![](https://assets.leetcode.com/uploads/2019/05/03/1336_ex1.JPG)

```
Input: grid = [[1,0,1],[0,0,0],[1,0,1]]
Output: 2
Explanation: The cell (1, 1) is as far as possible from all the land with distance 2.
```

**Example 2:**

![](https://assets.leetcode.com/uploads/2019/05/03/1336_ex2.JPG)

```
Input: grid = [[1,0,0],[0,0,0],[0,0,0]]
Output: 4
Explanation: The cell (2, 2) is as far as possible from all the land with distance 4.
```

**Constraints:**

- `n == grid.length`
- `n == grid[i].length`
- `1 <= n <= 100`
- `grid[i][j]` is `0` or `1`

```javascript
/**
 * @param {number[][]} grid
 * @return {number}
 */
var maxDistance = function(grid) {
  // 0 - water
  // 1 - land
  const n = grid.length;
  const distanceGrid = [];
  for (let i = 0; i < n; i++) {
    distanceGrid[i] = [];
    for (let j = 0; j < n; j++) {
      if (grid[i][j] === 1) {
        distanceGrid[i][j] = 0;
      } else {
        distanceGrid[i][j] = Number.MAX_SAFE_INTEGER;
      }
    }
  }

  // left-top
  for (let i = 0; i < n; i++) {
    for (let j = 0; j < n; j++) {
      if (grid[i][j] === 1) {
        continue;
      }
      if (i >= 1) {
        distanceGrid[i][j] = Math.min(distanceGrid[i][j], distanceGrid[i - 1][j] + 1);
      }
      if (j >= 1) {
        distanceGrid[i][j] = Math.min(distanceGrid[i][j], distanceGrid[i][j - 1] + 1);
      }
    }
  }

  // right-bottom
  for (let i = n - 1; i >= 0; i--) {
    for (let j = n - 1; j >= 0; j--) {
      if (grid[i][j] === 1) {
        continue;
      }
      if (i < n - 1) {
        distanceGrid[i][j] = Math.min(distanceGrid[i][j], distanceGrid[i + 1][j] + 1);
      }
      if (j < n - 1) {
        distanceGrid[i][j] = Math.min(distanceGrid[i][j], distanceGrid[i][j + 1] + 1);
      }
    }
  }

  let result = -1;
  for (let i = 0; i < n; i++) {
    for (let j = 0; j < n; j++) {
      if (grid[i][j] === 0) {
        result = Math.max(result, distanceGrid[i][j]);
      }
    }
  }

  return result === Number.MAX_SAFE_INTEGER ? -1 : result;
};
```
