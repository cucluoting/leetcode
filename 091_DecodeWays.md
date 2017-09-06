# 91. Decode Ways

A message containing letters from `A-Z` is being encoded to numbers using the following mapping:

```
'A' -> 1
'B' -> 2
...
'Z' -> 26
```

Given an encoded message containing digits, determine the total number of ways to decode it.

For example,  
Given encoded message `"12"`, it could be decoded as `"AB"` (1 2) or `"L"` (12).

The number of ways decoding `"12"` is 2.

友情链接：[70. Climbing Stairs](https://github.com/cucluoting/leetcode/blob/master/070_ClimbingStairs.md)

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var numDecodings = function(s) {
  if (!s) return 0

  var f1 = 1
  var f2 = s[0] === '0' ? 0 : 1
  if (s.length === 1) return f2

  for (var i = 2, len = s.length; i <= len; i++) {
    var f3 = s[i - 1] === '0' ? 0 : f2

    var tempNum = Number(s.slice(i - 2, i))
    if (tempNum >= 10 && tempNum <= 26) f3 += f1
    
    f1 = f2
    f2 = f3
  }
  return f2
};
```
