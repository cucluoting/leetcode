# 216. Combination Sum III

Find all possible combinations of k numbers that add up to a number n, given that only numbers from 1 to 9 can be used and each combination should be a unique set of numbers.

**Example 1:**

Input: k = 3, n = 7

Output:
```
[[1,2,4]]
```

**Example 2:**

Input: k = 3, n = 9

Output:
```
[[1,2,6], [1,3,5], [2,3,4]]
```

```javascript
/**
 * @param {number} k
 * @param {number} n
 * @return {number[][]}
 */
var combinationSum3 = function(k, n) {
  var result = []
  helper(n, 1, [], result, k)
  return result
};

var helper = function(target, start, currentItem, result, count) {
  if (count === 0) {
    if (target === 0) result.push(currentItem.slice(0))
    return
  }
  for (var i = start; i <= 9; i++) {
    currentItem.push(i)
    helper(target - i, i + 1, currentItem, result, count - 1)
    currentItem.pop()
  }
};
```
