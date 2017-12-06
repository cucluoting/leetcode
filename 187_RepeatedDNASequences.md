# 187. Repeated DNA Sequences

All DNA is composed of a series of nucleotides abbreviated as A, C, G, and T, for example: "ACGAATTCCG". When studying DNA, it is sometimes useful to identify repeated sequences within the DNA.

Write a function to find all the 10-letter-long sequences (substrings) that occur more than once in a DNA molecule.

For example,

```
Given s = "AAAAACCCCCAAAAACCCCCCAAAAAGGGTTT",

Return:
["AAAAACCCCC", "CCCCCAAAAA"].
```

```javascript
/**
 * @param {string} s
 * @return {string[]}
 */
var findRepeatedDnaSequences = function(s) {
  var result = []
  var map = {}
  var index = 0
  while (index + 10 <= s.length) {
    const substring = s.substr(index, 10)
    // 如果在字典里已经存在
    if (map[substring] !== undefined) {
      // 如果之前出现的次数为1，则加入到结果中
      if (map[substring] === 1) result.push(substring)
      map[substring] += 1
    } else {
      map[substring] = 1
    }
    index += 1
  }
  return result
};
```
