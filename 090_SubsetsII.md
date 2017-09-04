# 90. Subsets II

Given a collection of integers that might contain duplicates, nums, return all possible subsets.

**Note:** The solution set must not contain duplicate subsets.

For example,
If nums = `[1,2,2]`, a solution is:

```
[
  [2],
  [1],
  [1,2,2],
  [2,2],
  [1,2],
  []
]
```

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var subsetsWithDup = function(nums) {
  var result = []
  if (nums.length === 0) return result
  var tempNums = []
  nums.sort()
  helper(nums, tempNums, 0, result)
  return result
};

var helper = function(nums, item, start, result) {
  result.push(item.slice(0))

  for (var i = start; i < nums.length; i++) {
    if (i > start && nums[i] === nums[i - 1]) continue
    item.push(nums[i])
    helper(nums, item, i + 1, result)
    item.pop()
  }
};
```
