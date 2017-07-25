# 60. Permutation Sequence

The set `[1,2,3,…,n]` contains a total of n! unique permutations.

By listing and labeling all of the permutations in order,  
We get the following sequence (ie, for n = 3):

1. `"123"`
2. `"132"`
3. `"213"`
4. `"231"`
5. `"312"`
6. `"321"`

Given n and k, return the kth permutation sequence.

Note: Given n will be between 1 and 9 inclusive.

```javascript
/**
 * @param {number} n
 * @param {number} k
 * @return {string}
 */
var getPermutation = function(n, k) {
  var result = ''
  var nums = []
  var factorial = getFactorial(n - 1)

  for (var i = 1; i <= n; i++) {
    nums.push(i)
  } 

  k--

  for (var i = n - 1; i >= 0; i--) {
    var index = Math.floor(k / factorial)
    result += nums[index]
    nums.splice(index, 1)
    
    k %= factorial
    factorial /=  i
  }

  return result
};

var getFactorial = function(n) {
  var result = 1
  for (var i = 2; i <= n; i++) {
    result *= i
  }
  return result
};
```
