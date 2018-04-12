# 221. Maximal Square

Given a 2D binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

For example, given the following matrix:

```
1 0 1 0 0
1 0 1 1 1
1 1 1 1 1
1 0 0 1 0
```

Return 4.

```javascript
/**
 * @param {character[][]} matrix
 * @return {number}
 */
var maximalSquare = function(matrix) {
  if (!matrix.length || !matrix[0].length) return 0
  let result = 0
  let dp = []
  let row = matrix.length
  let col = matrix[0].length

  for (let i = 0; i < row; i++) {
    dp[i] = []
    for (let j = 0; j < col; j++) {
      if (matrix[i][j] === '1') {
        if (i === 0 || j === 0) {
          dp[i][j] = 1
        } else {
          // 以该点作为右下角，找出其他三个角的最小值并加一
          dp[i][j] = Math.min(dp[i - 1][j], dp[i][j - 1], dp[i - 1][j - 1]) + 1
        }
      } else {
        dp[i][j] = 0
      }
      result = Math.max(dp[i][j], result)
    }
  }
  return result * result
};
```
