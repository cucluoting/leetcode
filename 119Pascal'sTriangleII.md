# 119. Pascal's Triangle II

Given an index k, return the kth row of the Pascal's triangle.

For example, given k = 3,
Return `[1,3,3,1]`.

**Note:**
Could you optimize your algorithm to use only O(k) extra space?

```javascript
/**
 * @param {number} rowIndex
 * @return {number[]}
 */
var getRow = function(rowIndex) {
  var result = []
  for(var i = 0; i <= rowIndex; i++) {
    for(var k = i; k >= 0; k--) {
      if(k > 0 && k <= i - 1) {
        result[k] = result[k - 1] + result[k]
      }else {
        result[k] = 1
      }
    }
  }
  return result
};
```
