# 3. Longest Substring Without Repeating Characters

Given a string, find the length of the **longest substring** without repeating characters.

**Examples:**

Given `"abcabcbb"`, the answer is `"abc"`, which the length is 3.

Given `"bbbbb"`, the answer is `"b"`, with the length of 1.

Given `"pwwkew"`, the answer is `"wke"`, with the length of 3. Note that the answer must be a substring, `"pwke"` is a subsequence and not a substring.

- Brute Force(是我...
```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
  var longestLength = 0
  var len = s.length
  for(var i = 0; i < len; i++) {
    var tempStr = ''
    for(var j = i; j < len; j++) {
      if(tempStr.indexOf(s[j]) > -1) break
      tempStr += s[j]
    }
    if(tempStr.length > longestLength) longestLength = tempStr.length
  }
  return longestLength
};
```

- Sliding Window
```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
  var len = s.length
  var longestLength = 0, i = 0, j = 0
  var tempStr = ''
  while(i < len && j < len) {
    if(tempStr.indexOf(s[j]) < 0) {
      tempStr += s[j++]
      // i为开始位置，j为结束位置
      longestLength = Math.max(j - i, longestLength)
    }else {
      tempStr = tempStr.substring(1)
      i++
    }
  }
  return longestLength
};

```
