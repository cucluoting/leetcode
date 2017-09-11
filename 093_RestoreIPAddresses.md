# 93. Restore IP Addresses

Given a string containing only digits, restore it by returning all possible valid IP address combinations.

For example:  
Given `"25525511135"`,

return `["255.255.11.135", "255.255.111.35"]`. (Order does not matter)

```javascript
/**
 * @param {string} s
 * @return {string[]}
 */
var restoreIpAddresses = function(s) {
  var result = []
  var tempArr = []
  helper(s, 0, tempArr, result)
  return result
};

var helper = function(s, index, tempArr, result) {
  var length = s.length

  if (index === length && tempArr.length === 4) {
    result.push(tempArr.join('.'))
    return
  }

  // 位数限制
  if (length - index < 4 - tempArr.length) return
  if (length - index > 3 * (4 - tempArr.length)) return

  var tempNum = 0
  for (var i = index; i < index + 3 && i < s.length; i++) {
    tempNum = tempNum * 10 + Number(s[i])
    // 数值限制
    if (tempNum > 255) continue

    tempArr.push(s.slice(index, i + 1))
    helper(s, i + 1, tempArr, result)
    tempArr.pop()
    
    if (tempNum === 0) break
  }
}
```
