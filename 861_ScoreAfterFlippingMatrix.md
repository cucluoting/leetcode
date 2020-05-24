# 861. Score After Flipping Matrix

We have a two dimensional matrix A where each value is 0 or 1.

A move consists of choosing any row or column, and toggling each value in that row or column: changing all 0s to 1s, and all 1s to 0s.

After making any number of moves, every row of this matrix is interpreted as a binary number, and the score of the matrix is the sum of these numbers.

Return the highest possible score.


**Example 1:**
```
Input: [[0,0,1,1],[1,0,1,0],[1,1,0,0]]
Output: 39
Explanation:
Toggled to [[1,1,1,1],[1,0,0,1],[1,1,1,1]].
0b1111 + 0b1001 + 0b1111 = 15 + 9 + 15 = 39
```

**Note:**

1. 1 <= A.length <= 20
2. 1 <= A[0].length <= 20
3. A[i][j] is 0 or 1.

```javascript
/**
 * @param {number[][]} A
 * @return {number}
 */
var matrixScore = function(A) {
  const rows = A.length
  const cols = A[0].length
  let result = 0
  for (let col = 0; col < cols; col++) {
    let colCount = 0
    for (let row = 0; row < rows; row++) {
      colCount += A[row][col] ^ A[row][0]
    }
    result += Math.max(colCount, rows - colCount) * (1 << (cols - 1 - col))
  }
  return result
};
```
