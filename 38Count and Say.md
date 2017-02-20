# 38. Count and Say

The count-and-say sequence is the sequence of integers beginning as follows:  
`1, 11, 21, 1211, 111221, ...`  

`1` is read off as `"one 1"` or `11`.  
`11` is read off as `"two 1s"` or `21`.  
`21` is read off as `"one 2, then one 1"` or `1211`.  
Given an integer n, generate the nth sequence.  

Note: The sequence of integers will be represented as a string.

```javascript
/**
 * @param {number} n
 * @return {string}
 */
var countAndSay = function(n) {
  if(n === 1) return '1'
  var count = 2,
      result = '1',
      tempCount = 0,
      tempNum
  while(count <= n) {
    tempNum = result[0]
    tempCount = 1
    let newResult = ''
    for(var i = 1, len = result.length; i < len; i++) {
      if(result[i] === tempNum) {
        tempCount++
      }else {
        newResult += tempCount + tempNum
        tempNum = result[i]
        tempCount = 1
      }
    }
    newResult += tempCount + tempNum
    result = newResult
    count++
  }
  return result
};
```
