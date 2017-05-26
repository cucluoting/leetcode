# 6. ZigZag Conversion

The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

```
P   A   H   N
A P L S I I G
Y   I   R
```

And then read line by line: `"PAHNAPLSIIGYIR"`

Write the code that will take a string and make this conversion given a number of rows:

```
string convert(string text, int nRows);
```

`convert("PAYPALISHIRING", 3)` should return `"PAHNAPLSIIGYIR"`.


咦...我好像没有按数学规律写...
大概思路就是有几行就生成几个数组，按指定顺序推入不同行的数组就行了。

```javascript
/**
 * @param {string} s
 * @param {number} numRows
 * @return {string}
 */
var convert = function(s, numRows) {
  var operator = '+',
      index = 0,
      tempObj = {}
      resultStr = ''
  for(var i = 0; i < s.length; i++) {
    if(typeof tempObj[index] === 'undefined') tempObj[index] = []
    tempObj[index].push(s.charAt(i))

    if(operator === '+') {
      index++
    }else if(operator === '-') {
      index--
    }
    if(index === numRows) {
      index = numRows - 2
      operator = '-'
    }else if(index === -1) {
      index = 1
      operator = '+'
    }
  }
  for(var prop in tempObj) {
    resultStr += tempObj[prop].join('')
  }
  return resultStr
};
```
