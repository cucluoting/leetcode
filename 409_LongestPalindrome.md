# 409. Longest Palindrome

Given a string which consists of lowercase or uppercase letters, find the length of the longest palindromes that can be built with those letters.

This is case sensitive, for example "Aa" is not considered a palindrome here.

**Note:**
Assume the length of given string will not exceed 1,010.

**Example:**
```
Input:
"abccccdd"

Output:
7

Explanation:
One longest palindrome that can be built is "dccaccd", whose length is 7.
```

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var longestPalindrome = function(s) {
  const map = {}
  for (let i = 0; i < s.length; i++) {
    map[s[i]] = map[s[i]] ? map[s[i]] + 1 : 1
  }

  let count = 0
  let hasOdds = false
  for (const num of Object.values(map)) {
    if (num % 2 === 0) {
      count += num
    } else {
      count += num - 1
      hasOdds = true
    }
  }
  return hasOdds ? count + 1 : count
};
```
