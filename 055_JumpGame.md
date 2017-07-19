# 55. Jump Game

Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

For example:  
A = `[2,3,1,1,4]`, return `true`.

A = `[3,2,1,0,4]`, return `false`.

```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var canJump = function(nums) {
  if (nums.length === 0) return false
  var reach = 0
  var length = nums.length
  for (var i = 0; i <= Math.min(reach, length - 1); i++) {
    reach = Math.max(reach, nums[i] + i)
  }
  if (reach < length - 1) return false
  return true
};
```
