# 840. Magic Squares In Grid

A 3 x 3 magic square is a 3 x 3 grid filled with distinct numbers **from 1 to 9** such that each row, column, and both diagonals all have the same sum.

Given an grid of integers, how many 3 x 3 "magic square" subgrids are there?  (Each subgrid is contiguous).


**Example 1:**
```
Input: [[4,3,8,4],
        [9,5,1,9],
        [2,7,6,2]]
Output: 1
Explanation: 
The following subgrid is a 3 x 3 magic square:
438
951
276

while this one is not:
384
519
762

In total, there is only one magic square inside the given grid.
```
**Note:**

1. 1 <= grid.length <= 10
2. 1 <= grid[0].length <= 10
3. 0 <= grid[i][j] <= 15

```javascript
/**
 * @param {number[][]} grid
 * @return {number}
 */
var numMagicSquaresInside = function(grid) {
  let result = 0;
  for (let row = 0; row < grid.length - 2; row++) {
    for (let col = 0; col < grid[0].length - 2; col++) {
      if (grid[row + 1][col + 1] !== 5) {
        continue;
      }
      if (
        check(
          grid[row][col],
          grid[row][col + 1],
          grid[row][col + 2],
          grid[row + 1][col],
          grid[row + 1][col + 1],
          grid[row + 1][col + 2],
          grid[row + 2][col],
          grid[row + 2][col + 1],
          grid[row + 2][col + 2]
        )
      ) {
        result += 1;
      }
    }
  }
  return result;
};

var check = function(a, b, c, d, e, f, g, h, l) {
  const sum = a + b + c;
  return (
    [a, b, c, d, e, f, g, h, l].sort().every((value, i) => value === i + 1) &&
    d + e + f === sum &&
    g + h + l === sum &&
    a + d + g === sum &&
    b + e + h === sum &&
    c + f + l === sum &&
    a + e + l === sum &&
    c + e + g === sum
  );
};

```
