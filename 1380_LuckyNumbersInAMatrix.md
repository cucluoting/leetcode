# 1380. Lucky Numbers in a Matrix
Given a m * n matrix of distinct numbers, return all lucky numbers in the matrix in any order.

A lucky number is an element of the matrix such that it is the minimum element in its row and maximum in its column.

**Example 1:**
```
Input: matrix = [[3,7,8],[9,11,13],[15,16,17]]
Output: [15]
Explanation: 15 is the only lucky number since it is the minimum in its row and the maximum in its column
```
**Example 2:**
```
Input: matrix = [[1,10,4,2],[9,3,8,7],[15,16,17,12]]
Output: [12]
Explanation: 12 is the only lucky number since it is the minimum in its row and the maximum in its column.
```
**Example 3:**
```
Input: matrix = [[7,8],[1,2]]
Output: [7]
```

**Constraints:**

- m == mat.length
- n == mat[i].length
- 1 <= n, m <= 50
- 1 <= matrix[i][j] <= 10^5.
- All elements in the matrix are distinct.

```javascript
/**
 * @param {number[][]} matrix
 * @return {number[]}
 */
var luckyNumbers = function(matrix) {
  const minOfRows = []
  const maxOfCols = matrix[0]
  for (let i = 0; i < matrix.length; i++) {
    minOfRows[i] = matrix[i][0]
    for (let j = 0; j < matrix[i].length; j++) {
      minOfRows[i] = Math.min(minOfRows[i], matrix[i][j])
      maxOfCols[j] = Math.max(maxOfCols[j], matrix[i][j])
    }
  }
  const result = []
  for (let i = 0; i < minOfRows.length; i++) {
    for (let j = 0; j < maxOfCols.length; j++) {
      if (minOfRows[i] === maxOfCols[j]) {
        result.push(minOfRows[i])
      }
    }
  }
  return result
};
```
