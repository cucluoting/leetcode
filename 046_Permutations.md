# 46. Permutations

Given a collection of **distinct** numbers, return all possible permutations.

For example,
`[1,2,3]` have the following permutations:

```
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

友情链接：[CombinationSum](https://github.com/cucluoting/leetcode/blob/master/039_CombinationSum.md), [Next Permutation](https://github.com/cucluoting/leetcode/blob/master/031_NextPermutation.md)

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permute = function(nums) {
  var result = []
  var tempNums = []
  var used = []
  helper(nums, used, tempNums, result)

  return result
};

var helper = function(nums, used, item, result) {
  if (item.length === nums.length) {
    result.push(item.slice(0))
    return
  }
  for (var i = 0; i < nums.length; i++) {
    if (!used[i]) {
      used[i] = true
      item.push(nums[i])
      helper(nums, used, item, result)
      item.pop()
      used[i] = false
    }
  }
};
```
