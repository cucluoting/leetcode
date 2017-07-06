# 47. Permutations II
Given a collection of numbers that might contain duplicates, return all possible unique permutations.

For example,  
`[1,1,2]` have the following unique permutations:

```
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]
````

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permuteUnique = function(nums) {
  var result = []
  var tempNums = []
  var used = []
  nums.sort(function(a, b) {
    return a - b
  })
  helper(nums, used, tempNums, result)

  return result
};

var helper = function(nums, used, item, result) {
  if (item.length === nums.length) {
    result.push(item.slice(0))
    return
  }
  for (var i = 0; i < nums.length; i++) {
    // 如果前面的相同元素还没有用过，就跳过
    if (i > 0 && nums[i] === nums[i - 1] && !used[i - 1]) continue
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
