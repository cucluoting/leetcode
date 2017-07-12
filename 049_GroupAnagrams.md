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
  for (var i = 0; i < strs.length; i++) {
    var tempArr = strs[i].split('')
    tempArr.sort()
    var key = tempArr.join('')
    if (!map[key]) {
      map[key] = []
    }
    map[key].push(strs[i])
  }
  for(var key in map) {
    result.push(map[key])
  }
  return result
};

```
