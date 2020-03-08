# 867. Transpose Matrix

Given a matrix A, return the transpose of A.

The transpose of a matrix is the matrix flipped over it's main diagonal, switching the row and column indices of the matrix.

![](https://assets.leetcode.com/uploads/2019/10/20/hint_transpose.png)

**Example 1:**
```
Input: [[1,2,3],[4,5,6],[7,8,9]]
Output: [[1,4,7],[2,5,8],[3,6,9]]
```
**Example 2:**
```
Input: [[1,2,3],[4,5,6]]
Output: [[1,4],[2,5],[3,6]]
```

**Note:**

1. 1 <= A.length <= 1000
2. 1 <= A[0].length <= 1000

```javascript
/**
 * @param {number[][]} A
 * @return {number[][]}
 */
var transpose = function(A) {
  const result = []
  for (let i = 0; i < A.length; i++) {
    for (let j = 0; j < A[i].length; j++) {
      if (!result[j]) {
        result[j] = []
      }
      result[j][i] = A[i][j]
    }
  }
  return result
};
```
