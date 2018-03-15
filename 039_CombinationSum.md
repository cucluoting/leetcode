# 39. Combination Sum

Given a set of candidate numbers (C) (without duplicates) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

The same repeated number may be chosen from C unlimited number of times.

**Note:**
- All numbers (including target) will be positive integers.
- The solution set must not contain duplicate combinations.

For example, given candidate set `[2, 3, 6, 7]` and target `7`, 

A solution set is: 
```
[
  [7],
  [2, 2, 3]
]
```

```javascript
/**
 * @param {number[]} candidates
 * @param {number} target
 * @return {number[][]}
 */
var combinationSum = function(candidates, target) {
  var result = []
  if (candidates.length === 0) return result

  var currentItem = []
  candidates.sort(function(a, b) {
    return a - b
  })
  helper(candidates, target, 0, currentItem, result)
  return result
};

var helper = function(candidates, target, start, currentItem, result) {
  if (target < 0) return
  if (target === 0) {
    // currentItem.slice(0)而不是currentItem（复制到一个新数组中
    result.push(currentItem.slice(0))
    return
  }
  for (var i = start; i < candidates.length; i++) {
    if (candidates[i] === candidates[i - 1]) continue
    currentItem.push(candidates[i])
    helper(candidates, target - candidates[i], i, currentItem, result)
    currentItem.pop()
  }
};
```
