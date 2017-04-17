# 136. Single Number

Given an array of integers, every element appears twice except for one. Find that single one.

**Note:**
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?


天啊。。。我当年学数电的时候就觉得这东西没用。。。结果还是打脸了。。。  
居然能用异或的方法解决这题。。。  

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
  if(nums.length < 1) return 0   
  var result = nums[0]
  for(var i = 1, len = nums.length; i < len; i++) {
    result ^= nums[i]
  }
  return result
};
```
