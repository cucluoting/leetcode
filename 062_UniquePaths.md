# 62. Unique Paths

A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

![](https://leetcode.com/static/images/problemset/robot_maze.png)

Above is a 3 x 7 grid. How many possible unique paths are there?

Note: m and n will be at most 100.


公式为`f[i][j] = f[i - 1][j] + f[i][j - 1]`

```javascript
/**
 * @param {number} m
 * @param {number} n
 * @return {number}
 */
var uniquePaths = function(m, n) {
  var pathsArr = []

  for (var i = 0; i < m; i++) {
    pathsArr[i] = []
    pathsArr[i][0] = 1
  }
  for (var i = 0; i < n; i++) {
    pathsArr[0][i] = 1
  }
  for (var i = 1; i < m; i++) {
    for (var j = 1; j < n; j++) {
      pathsArr[i][j] = pathsArr[i - 1][j] + pathsArr[i][j - 1]
    }
  }
  return pathsArr[m - 1][n - 1]
};
```

优化——

```javascript
/**
 * @param {number} m
 * @param {number} n
 * @return {number}
 */
var uniquePaths = function(m, n) {
  var pathsArr = []
  pathsArr[0] = 1
  for (var i = 1; i < n; i++) {
    pathsArr[i] = 0
  }
  for (var i = 0; i < m; i++) {
    for (var j = 1; j < n; j++) {
      // pathsArr[j]相当于f[i - 1][j], pathsArr[j - 1]相当于f[i][j - 1]
      pathsArr[j] += pathsArr[j - 1]
    }
  }
  return pathsArr[n - 1]
};
```
