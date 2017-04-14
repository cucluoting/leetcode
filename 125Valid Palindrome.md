# 125. Valid Palindrome

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.  

For example,  
`"A man, a plan, a canal: Panama"` is a palindrome.  
`"race a car"` is not a palindrome.  

Note:  
Have you consider that the string might be empty? This is a good question to ask during an interview.  

For the purpose of this problem, we define empty string as valid palindrome.  

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isPalindrome = function(s) {
  s = s.toLowerCase()
  if(s.length < 2) return true
  var left = 0
  var right = s.length - 1
  while(left < right) {
    if(!/[A-Za-z0-9]/.test(s.charAt(left))) {
      left++
      continue
    }
    if(!/[A-Za-z0-9]/.test(s.charAt(right))) {
      right--
      continue
    }
    if(s.charAt(left) !== s.charAt(right)) {
      return false
    }
    left++
    right--
  }
  return true
};
```
