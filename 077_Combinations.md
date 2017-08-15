# 77. Combinations

Given two integers n and k, return all possible combinations of k numbers out of 1 ... n.

For example,  
If n = 4 and k = 2, a solution is:

```
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
```

```javascript
/**
 * @param {number} n
 * @param {number} k
 * @return {number[][]}
 */
var combine = function(n, k) {
  var result = []
  if (n < k || n <= 0) return result
  var tempNums = []
  helper(n, k, tempNums, 1, result)
  return result
};

var helper = function(n, k, item, start, result) {
  if (item.length === k) {
    result.push(item.slice(0))
    return
  }
  for (var i = start; i <= n; i++) {
    item.push(i)
    helper(n, k, item, i + 1, result)
    item.pop()
  }
}
```
