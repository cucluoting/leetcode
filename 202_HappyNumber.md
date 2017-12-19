# 202. Happy Number

Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

**Example**: 19 is a happy number

12 + 92 = 82  
82 + 22 = 68  
62 + 82 = 100  
12 + 02 + 02 = 1  


```javascript
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function(n) {
  // 所有不快乐数的平方和进入的循环中都有4
  while (n !== 1 && n !== 4) {
    var sum = 0
    while (n) {
      sum += Math.pow(n % 10, 2)
      n = Math.floor(n / 10)
    }
    n = sum
  }
  return n === 1
};
```

```javascript
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function(n) {
  var set = []
  while (n !== 1) {
    var sum = 0
    while (n) {
      sum += Math.pow(n % 10, 2)
      n = Math.floor(n / 10)
    }
    // 只要结果集中出现过该数，则说明进入到了循环中
    if (set.indexOf(sum) > -1) return false
    set.push(sum)
    n = sum
  }
  return true
};
```
