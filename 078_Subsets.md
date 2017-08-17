# 78. Subsets

Given a set of **distinct** integers, nums, return all possible subsets.

**Note:** The solution set must not contain duplicate subsets.

For example,  
If **nums** = [1,2,3], a solution is:

```
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var subsets = function(nums) {
  var result = []
  if (nums.length === 0) return result
  var tempNums = []
  helper(nums, tempNums, 0, result)
  return result
};

var helper = function(nums, item, start, result) {
  result.push(item.slice(0))

  for (var i = start; i < nums.length; i++) {
    item.push(nums[i])
    helper(nums, item, i + 1, result)
    item.pop()
  }
}
```
