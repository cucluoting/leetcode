# 191. Number of 1 Bits

Write a function that takes an unsigned integer and returns the number of ’1' bits it has (also known as the [Hamming weight](https://en.wikipedia.org/wiki/Hamming_weight)).

For example, the 32-bit integer ’11' has binary representation `00000000000000000000000000001011`, so the function should return 3.

`n & (n - 1)`会把n最后一个1抵消掉

```javascript
/**
 * @param {number} n - a positive integer
 * @return {number}
 */
var hammingWeight = function(n) {
  var count = 0
  while(n !== 0) {
    count++
    n = n & (n - 1)
  }
  return count
};
```
