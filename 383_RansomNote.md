# 383. Ransom Note

Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

**Note:**
You may assume that both strings contain only lowercase letters.
```
canConstruct("a", "b") -> false
canConstruct("aa", "ab") -> false
canConstruct("aa", "aab") -> true
```

解题思路：在`magazine`里查找`ransomNote`里的字母，因为`magazine`里同样的字母只能用一次，所以找一个就要删除一个，找不到了直接`return false`

```javascript
/**
 * @param {string} ransomNote
 * @param {string} magazine
 * @return {boolean}
 */
var canConstruct = function(ransomNote, magazine) {
  if (ransomNote.length > magazine.length) return false
  if (ransomNote.length > 0 && magazine.length === 0) return false
  
  const ransomNoteArr = ransomNote.split('')
  const magazineArr = magazine.split('')
  for (let i = 0; i < ransomNoteArr.length; i++) {
    const index = magazineArr.indexOf(ransomNoteArr[i])
    if (index === -1) {
      return false
    } else {
      magazineArr.splice(index, 1)
    }
  }
  return true
};
```
