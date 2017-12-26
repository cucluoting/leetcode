# 204. Count Primes

**Description:**

Count the number of prime numbers less than a non-negative number, **n**.

解法：[Sieve of Eratosthenes](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes)

![image](https://upload.wikimedia.org/wikipedia/commons/b/b9/Sieve_of_Eratosthenes_animation.gif)

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var countPrimes = function(n) {
  // 先将所有数值假定为质数
  var primes = Array(n).fill(true)
  var result = 0
  for (var i = 2; i < n; i++) {
    if (primes[i]) {
      ++result
      // 将当前质数的各个倍数值都设为非质数，剩下的就是质数了
      for (var j = 2; j * i < n; j++) {
        primes[j * i] = false
      }
    }
  }
  return result
};
```
