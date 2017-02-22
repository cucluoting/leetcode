# 53. Maximum Subarray

Find the contiguous subarray within an array (containing at least one number) which has the largest sum.

For example, given the array `[-2,1,-3,4,-1,2,1,-5,4]`,  
the contiguous subarray `[4,-1,2,1]` has the largest sum = `6`.  

**More practice:**  
If you have figured out the O(n) solution, try coding another solution using the divide and conquer approach, which is more subtle.


动态规划的解法：  
思路：  
记录两个和，一个局部的，一个全局的。   
局部的：将第i个值，跟之前的子序列和与第i个值的和作比较，如果第i个值更大，则相当于另起一个子序列，否则还是原来的子序列。  
全局的：一旦局部的比全局的大，则替换。  


```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxSubArray = function(nums) {
  var tempSun = nums[0],
      result = nums[0]
  for(var i = 1, len = nums.length; i < len; i++) {
    tempSun = Math.max(nums[i], tempSun + nums[i])
    result = Math.max(result, tempSun)
  }
  return result
};
```
