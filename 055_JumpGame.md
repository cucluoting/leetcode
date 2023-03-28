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
  let k = 0;
  for (let i = 0; i < nums.length; i++) {
    if (i > k) {
      return false;
    }
    k = Math.max(k, i + nums[i]);
  }
  return true;
};
```
