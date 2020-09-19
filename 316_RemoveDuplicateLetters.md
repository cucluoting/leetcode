# 316. Remove Duplicate Letters

Given a string which contains only lowercase letters, remove duplicate letters so that every letter appears once and only once. You must make sure your result is the smallest in lexicographical order among all possible results.

**Example 1:**
```
Input: "bcabc"
Output: "abc"
```

**Example 2:**
```
Input: "cbacdcbc"
Output: "acdb"
```

**Note:** This question is the same as 1081: https://leetcode.com/problems/smallest-subsequence-of-distinct-characters/

一个一个字符处理
```javascript
/**
 * @param {string} s
 * @return {string}
 */
var removeDuplicateLetters = function(s) {
  const aCode = 'a'.charCodeAt()
  const arr = []
  let pos = 0
  for (let i = 0; i < s.length; i++) {
    arr[s.charCodeAt(i) - aCode] = arr[s.charCodeAt(i) - aCode] ? arr[s.charCodeAt(i) - aCode] + 1 : 1
  }
  for (let i = 0; i < s.length; i++) {
    if (s.charCodeAt(i) < s.charCodeAt(pos)) {
      pos = i
    }
    if (--arr[s.charCodeAt(i) - aCode] === 0) {
      break
    }
  }
  const newStr = s.substring(pos + 1).split('').filter(v => v !== s[pos]).join('')
  return s.length === 0 ? '' : s[pos] + removeDuplicateLetters(newStr)
};
```

用栈处理
```javascript
/**
 * @param {string} s
 * @return {string}
 */
var removeDuplicateLetters = function(s) {
  const aCode = 'a'.charCodeAt()
  const seen = new Set()
  const last = []
  const stack = []
  let pos = 0
  for (let i = 0; i < s.length; i++) {
    last[s.charCodeAt(i) - aCode] = i
  }
  for (let i = 0; i < s.length; i++) {
    pos = s.charCodeAt(i) - aCode
    if (seen.has(pos)) {
      continue
    }
    seen.add(pos)
    while (stack.length && stack[stack.length - 1] > pos && i < last[stack[stack.length - 1]]) {
      seen.delete(stack.pop())
    }
    stack.push(pos)
  }
  let result = ''
  for (let i = 0; i < stack.length; i++) {
    result += String.fromCharCode(stack[i] + aCode)    
  }
  return result
};
```
