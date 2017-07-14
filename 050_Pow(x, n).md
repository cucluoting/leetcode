# 50. Pow(x, n)

Implement pow(x, n).

二分法

```javascript
/**
 * @param {number} x
 * @param {number} n
 * @return {number}
 */
var myPow = function(x, n) {
  if (n === 0) return 1

  var half = myPow(x, parseInt(n / 2))
  if (n % 2 === 0) {
    return half * half
  } else if (n > 0) {
    return half * half * x
  } else {
    return half * half * (1 / x)
  }
};
```
