# 131. Palindrome Partitioning

Given a string s, partition s such that every substring of the partition is a palindrome.

Return all possible palindrome partitioning of s.

For example, given s = `"aab"`,  
Return  
```
[
  ["aa","b"],
  ["a","a","b"]
]
```

```javascript
/**
 * @param {string} s
 * @return {string[][]}
 */
var partition = function(s) {
  var result = []
  dfs(s, result, [], 0)
  return result
};

var dfs = function(s, result, path, pos) {
  if (pos === s.length) {
    result.push(path.slice())
    return
  }
  for (var i = pos; i < s.length; i++) {
    if (isPalindrome(s, pos, i)) {
      path.push(s.substring(pos, i + 1))
      dfs(s, result, path, i + 1)
      path.pop(path.length - 1)
    }
  }
};

var isPalindrome = function(s, start, end) {
  while (start < end) {
    if (s[start] !== s[end]) return false
    ++start
    --end
  }
  return true
};
```
