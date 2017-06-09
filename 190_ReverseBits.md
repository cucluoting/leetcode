# 190. Reverse Bits

Reverse bits of a given 32 bits unsigned integer.

For example, given input 43261596 (represented in binary as **00000010100101000001111010011100**), 
return 964176192 (represented in binary as **00111001011110000010100101000000**).

[按位操作符](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators#Bitwise_AND)


```javascript
/**
 * @param {number} n - a positive integer
 * @return {number} - a positive integer
 */
var reverseBits = function(n) {
  var result = 0
  var sign = 0
  for(var i = 0; i < 32; i++) {
    if(i === 0) {
      // js中的整数是有符号的32位整数，所以需要手动换算符号位
      sign = (n & 1)
      result = result << 1
    }else {
      result = result << 1 | (n & 1)
    }
    n = n >>> 1
  }
  result += sign * Math.pow(2, 31)
  return result
};
```
