# 118. Pascal's Triangle

Given numRows, generate the first numRows of Pascal's triangle.

For example, given numRows = 5,
Return

```
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```


```javascript
/**
 * @param {number} numRows
 * @return {number[][]}
 */
var generate = function(numRows) {
  var result = []
  for(var i = 0; i < numRows; i++) {
    result[i] = []
    for(var k = 0; k <= i; k++) {
      if(k > 0 && k <= i - 1) {
        result[i][k] = result[i - 1][k - 1] + result[i - 1][k]
      }else {
        result[i][k] = 1
      }
    }
  }
  return result
};

```
