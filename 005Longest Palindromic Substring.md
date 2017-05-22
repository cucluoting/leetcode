# 5. Longest Palindromic Substring

Given a string **s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s** is 1000.

**Example:**

```
Input: "babad"

Output: "bab"

Note: "aba" is also a valid answer.
```


**Example:**

```
Input: "cbbd"

Output: "bb"
```

```javascript
/**
 * @param {string} s
 * @return {string}
 */
var longestPalindrome = function(s) {
  if(s.length < 1) return ''
  var tempArr = []
  var maxLength = 0
  var result = ''
  for(var i = 0, len = s.length; i < len; i++) {
    tempArr.push(new Array(len))
  }
  for(var i = s.length - 1; i >= 0; i--) {
    for(var j = i; j < s.length; j++) {
      if(s[i] === s[j] && (j - i <= 2 || tempArr[i + 1][j - 1])) {
        tempArr[i][j] = true
        if(maxLength < j - i + 1) {
          maxLength = j - i + 1
          result = s.substring(i, j + 1)
        }
      }
    }
  }
  return result
};
```

- Manacher's Algorithm

  这个有点难理解了，看了好多分析文章才找到一个比较能看懂的-->https://segmentfault.com/a/1190000003914228

```javascript
/**
 * @param {string} s
 * @return {string}
 */
var longestPalindrome = function(s) {
  var t = '*#'
  // 将字符串处理成奇数长度的数组，不影响原字符串的回文性
  for(var i = 0, len = s.length; i < len; i++) {
    t += s[i] + '#'
  }

  // 记录以每一个元素为对称轴的回文半径
  var radius = []

  var maxRight = 0 // 回文子字符串的最大位置
  var pos = 0 // maxRight的回文对称轴

  var resultRadius = 0 // 最大回文半径
  var resultPos = 0 // 最大回文对称轴

  for(var i = 0, len = t.length; i < len; i++) {

    // i关于pos的对称点是2 * pos - i
    // 如果该点在当前子回文字符串范围内，则取该点对称位置的回文半径，但有可能这个半径太大以至于超过原来的子回文串范围，所以取两者的最小值
    // 如果该点不在范围内则需自行计算
    radius[i] = maxRight > i ? Math.min(radius[2 * pos - i], maxRight - i) : 1

    // 扩展子回文串范围得到当前元素作为回文对称轴的最大回文半径
    while(t[i + radius[i]] === t[i - radius[i]]) radius[i]++
    
    // 如果计算当前回文范围超出上一个范围时则更新范围
    if(maxRight < i + radius[i] - 1) {
      maxRight = i + radius[i] - 1
      pos = i
    }
    // 更新最大回文半径及回文对称轴
    if(resultRadius <= radius[i]) {
      resultRadius = radius[i]
      resultPos = i
    }
  }
  return s.substr(Math.floor((resultPos - resultRadius) / 2), resultRadius - 1)
};
```
