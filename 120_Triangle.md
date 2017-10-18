# 120. Triangle

Given a triangle, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.

For example, given the following triangle

```
[
     [2],
    [3,4],
   [6,5,7],
  [4,1,8,3]
]
```

The minimum path sum from top to bottom is 11 (i.e., 2 + 3 + 5 + 1 = 11).

**Note:**
Bonus point if you are able to do this using only O(n) extra space, where n is the total number of rows in the triangle.

```javascript
/**
 * @param {number[][]} triangle
 * @return {number}
 */
var minimumTotal = function(triangle) {
  var row = triangle.length
  var tempArr = triangle[row - 1]
  
  for (var i = row - 2; i >= 0; i--) {
    for (var j = 0; j <= i; j++) {
      tempArr[j] = triangle[i][j] + Math.min(tempArr[j], tempArr[j + 1])
    }
  }
  return tempArr[0]
};

```
