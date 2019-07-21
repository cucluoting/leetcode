# 345. Reverse Vowels of a String
Write a function that takes a string as input and reverse only the vowels of a string.

**Example 1:**
```
Input: "hello"
Output: "holle"
```
**Example 2:**
```
Input: "leetcode"
Output: "leotcede"
```

**Note:**
The vowels does not include the letter "y".

```javascript
/**
 * @param {string} s
 * @return {string}
 */
var reverseVowels = function(s) {
  let left = 0
  let right = s.length - 1
  let arr = s.split('')
  while (left < right) {
    if (isVowels(arr[left])) {
      if (isVowels(arr[right])) {
        const temp = arr[left]
        arr[left] = arr[right]
        arr[right] = temp
        left++
      }
      right--
    } else {
      left++
    }
  }
  return arr.join('')
};

var isVowels = function(c) {
  return 'aeiouAEIOU'.includes(c)
}
```
