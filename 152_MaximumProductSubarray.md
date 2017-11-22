# 152. Maximum Product Subarray

Find the contiguous subarray within an array (containing at least one number) which has the largest product.

For example, given the array `[2,3,-2,4]`,  
the contiguous subarray `[2,3]` has the largest product = `6`.

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxProduct = function(nums) {
  var result = nums[0]
  var max = nums[0]
  var min = nums[0]
  for (var i = 1, len = nums.length; i < len; i++) {
    var tempMax = max
    max = Math.max(tempMax * nums[i], min * nums[i], nums[i])
    min = Math.min(tempMax * nums[i], min * nums[i], nums[i])
    result = Math.max(max, result)
  }
  return result
};
```
