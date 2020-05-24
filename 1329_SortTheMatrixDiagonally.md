# 1329. Sort the Matrix Diagonally

Given a m * n matrix mat of integers, sort it diagonally in ascending order from the top-left to the bottom-right then return the sorted array.

 

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/01/21/1482_example_1_2.png)

```
Input: mat = [[3,3,1,1],[2,2,1,2],[1,1,1,2]]
Output: [[1,1,1,1],[1,2,2,2],[1,2,3,3]]
```

**Constraints:**

- m == mat.length
- n == mat[i].length
- 1 <= m, n <= 100
- 1 <= mat[i][j] <= 100


```javascript
/**
 * @param {number[][]} mat
 * @return {number[][]}
 */
var diagonalSort = function(mat) {
  const m = mat.length
  const n = mat[0].length
  const map = []
  for (let i = 0; i < m; i++) {
    for (let j = 0; j < n; j++) {
      if (!map[i - j + n]) {
        map[i - j + n] = []
      }
      map[i - j + n].push(mat[i][j])
    }
  }
  for (let i = 0; i < map.length; i++) {
    map[i]?.sort((a, b) => a - b)
  }
  for (let i = 0; i < m; i++) {
    for (let j = 0; j < n; j++) {
      mat[i][j] = map[i - j + n].shift()
    }
  }
  return mat
};
```
