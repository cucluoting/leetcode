# 40. Combination Sum II

Given a collection of candidate numbers (C) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

Each number in C may only be used once in the combination.

**Note:**
All numbers (including target) will be positive integers.

The solution set must not contain duplicate combinations.

For example, given candidate set `[10, 1, 2, 7, 6, 1, 5]` and target `8`, 

A solution set is: 

```
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]
```


```javascript
/**
 * @param {number[]} candidates
 * @param {number} target
 * @return {number[][]}
 */
var combinationSum2 = function(candidates, target) {
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
    result.push(currentItem.slice(0))
    return
  }
  for (var i = start; i < candidates.length; i++) {
    if(i > start && candidates[i] === candidates[i - 1]) continue
    currentItem.push(candidates[i])
    helper(candidates, target - candidates[i], i + 1, currentItem, result)
    currentItem.pop()
  }
};
```
