# 9. Palindrome Number

Determine whether an integer is a palindrome. Do this without extra space.

**Some hints:**
Could negative integers be palindromes? (ie, -1)

If you are thinking of converting the integer to string, note the restriction of using extra space.

You could also try reversing an integer. However, if you have solved the problem "Reverse Integer", you know that the reversed integer might overflow. How would you handle such case?

There is a more generic way of solving this problem.


- wikipedia----->回文数是指一个像16461这样“对称”的数，即：将这个数的数字按相反的顺序重新排列后，所得到的数和原来的数一样。
负数不是回文数？0是回文数？

其实这个题跟Reverse Integer一样的...

同·歪门邪道写法
```javascript
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
  if(x < 0) {
    return false
  }else if(x === 0) {
    return true
  }else {
    var tempArr = (x + '').split('').reverse(),
        tempStr = '',
        result
    tempStr = tempArr.join('')
    result = parseInt(tempStr, 10) === x ? true : false
    return result
  }
};
```
同·正统写法
```javascript
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
  if(x < 0) {
    return false
  }else if(x === 0) {
    return true
  }else {
    var INT_MAX = (2**31) - 1,
        tempx = x,
        reverseNum = 0
    while(tempx !== 0) {
      if(reverseNum > (INT_MAX - tempx % 10) / 10) return false
      reverseNum = tempx % 10 + reverseNum * 10
      tempx = parseInt(tempx / 10)
    }
    return x === reverseNum ? true : false
  }
};
```
