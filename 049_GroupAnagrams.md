# 49. Group Anagrams

Given an array of strings, group anagrams together.

For example, given: `["eat", "tea", "tan", "ate", "nat", "bat"]`, 

Return:
```
[
  ["ate", "eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

**Note:** All inputs will be in lower-case.

```javascript
/**
 * @param {string[]} strs
 * @return {string[][]}
 */
var groupAnagrams = function(strs) {
  var result = []
  var map = {}
  strs.forEach(function (str) {
    var key = str.split('').sort().join('')
    if (map[key] === undefined) {
      map[key] = result.length
      result[map[key]] = []
    }
    result[map[key]].push(str)
  })
  return result
};
```
