# 213. House Robber II

**Note**: This is an extension of House Robber.

After robbing those houses on that street, the thief has found himself a new place for his thievery so that he will not get too much attention. This time, all houses at this place are **arranged in a circle**. That means the first house is the neighbor of the last one. Meanwhile, the security system for these houses remain the same as for those in the previous street.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight **without alerting the police**.


```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var rob = function(nums) {
  if (nums.length < 2) return nums[0] || 0
  // 因为是环形，所以不能同时取头和尾
  return Math.max(helper(nums, 0, nums.length - 2), helper(nums, 1, nums.length - 1))
};

var helper = function(nums, start, end) {
  if (end - start < 2) return nums[start] || 0
  var per = 0
  var cur = 0
  for (var i = start; i <= end; i++) {
    var temp = cur
    cur = Math.max(temp, per + nums[i])
    per = temp
  }
  return Math.max(per, cur)
}
```
