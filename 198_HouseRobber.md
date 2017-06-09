# 198. House Robber

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and **it will automatically contact the police if two adjacent houses were broken into on the same night.**

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight **without alerting the police.**

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var rob = function(nums) {
  if(nums.length < 2) return nums[0] || 0
  var dps = []
  dps[0] = nums[0]
  dps[1] = Math.max(nums[0], nums[1])
  nums.forEach(function(num, index, nums) {
    if(index > 1) {
      dps[index] = Math.max(num + dps[index - 2], dps[index - 1])
    }
  })
  return dps[dps.length - 1]
};
```
