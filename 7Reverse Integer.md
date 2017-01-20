# 7. Reverse Integer

Reverse digits of an integer.
```
Example1: x = 123, return 321
Example2: x = -123, return -321
```

**Have you thought about this?**
Here are some good questions to ask before coding. Bonus points for you if you have already thought through this!

If the integer's last digit is 0, what should the output be? ie, cases such as 10, 100.

Did you notice that the reversed integer might overflow? Assume the input is a 32-bit integer, then the reverse of 1000000003 overflows. How should you handle such cases?

For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.


去看了一下别人的答案就觉得我的解法简直是歪门邪道...😷

```javascript
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
  var tempArr = (x + '').split('').reverse(),
      INT_MIN = - (2**31),
      INT_MAX = (2**31) - 1,
      tempStr = '',
      result
  if(tempArr[tempArr.length - 1] === '-') {
    tempArr.pop()
    tempArr.unshift('-')
  }
  tempStr = tempArr.join('')
  result = parseInt(tempStr, 10)
  if(result <= INT_MIN || result >= INT_MAX) {
    result = 0
  }
  return result
};
```


去学习了正统写法以后...
```javascript
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
  var INT_MIN = - (2**31),
      INT_MAX = (2**31) - 1,
      tempx = Math.abs(x),
      result = 0
  if(x === INT_MIN) return 0
  while(tempx !== 0) {
    // 在result溢出前作判断！！！
    if(result > (INT_MAX - tempx %10) / 10) return 0
    result = tempx % 10 + result * 10
    tempx = parseInt(tempx / 10)
  }
  return x > 0 ? result : -result
};
```
