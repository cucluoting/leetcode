# 306. Additive Number

Additive number is a string whose digits can form additive sequence.

A valid additive sequence should contain **at least** three numbers. Except for the first two numbers, each subsequent number in the sequence must be the sum of the preceding two.

Given a string containing only digits `'0'-'9'`, write a function to determine if it's an additive number.

Note: Numbers in the additive sequence cannot have leading zeros, so sequence `1, 2, 03` or `1, 02, 3` is invalid.

**Example 1:**
```
Input: "112358"
Output: true 
Explanation: The digits can form an additive sequence: 1, 1, 2, 3, 5, 8. 
             1 + 1 = 2, 1 + 2 = 3, 2 + 3 = 5, 3 + 5 = 8
```
**Example 2:**
```
Input: "199100199"
Output: true 
Explanation: The additive sequence is: 1, 99, 100, 199. 
             1 + 99 = 100, 99 + 100 = 199
```

**Follow up:**
How would you handle overflow for very large input integers?

```javascript
/**
 * @param {string} num
 * @return {boolean}
 */
var isAdditiveNumber = function(num) {
  for (let i = 1; i < num.length; i++) {
    let s1 = num.substr(0, i)
    if (s1.length > 1 && s1[0] === '0') {
      break
    }
    for (let j = i + 1; j < num.length; j++) {
      let s2 = num.substr(i, j - i)
      let d1 = Number(s1)
      let d2 = Number(s2)
      if (s2.length > 1 && s2[0] === '0') {
        break
      }
      let next = d1 + d2
      let nextStr = next.toString()
      if (nextStr !== num.substr(j, nextStr.length)) {
        continue
      }
      let currStr = s1 + s2 + nextStr
      while(currStr.length < num.length) {
        d1 = d2
        d2 = next
        next = d1 + d2
        nextStr = next.toString()
        currStr += nextStr
      }
      if (currStr === num) {
        return true
      }
    }
  }
  return false
};

```
