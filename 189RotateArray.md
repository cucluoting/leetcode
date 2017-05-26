# 189. Rotate Array

Rotate an array of n elements to the right by k steps.

For example, with n = 7 and k = 3, the array `[1,2,3,4,5,6,7]` is rotated to `[5,6,7,1,2,3,4]`.

**Note:**
Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.

**Hint:**
Could you do it in-place with O(1) extra space?


```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var rotate = function(nums, k) {
  k %= nums.length
  reverse(nums, 0, nums.length - 1)
  reverse(nums, 0, k - 1)
  reverse(nums, k, nums.length - 1)
};

var reverse = function(nums, start, end) {
  while(start < end) {
    var temp = nums[start]
    nums[start] = nums[end]
    nums[end] = temp
    start++
    end--
  }
}
```
