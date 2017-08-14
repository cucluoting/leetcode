# 75. Sort Colors

Given an array with n objects colored red, white or blue, sort them so that objects of the same color are adjacent, with the colors in the order red, white and blue.

Here, we will use the integers 0, 1, and 2 to represent the color red, white, and blue respectively.

**Note:**
You are not suppose to use the library's sort function for this problem.

**Follow up:**  
A rather straight forward solution is a two-pass algorithm using counting sort.
First, iterate the array counting number of 0's, 1's, and 2's, then overwrite array with total number of 0's, then 1's and followed by 2's.

Could you come up with an one-pass algorithm using only constant space?

```javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var sortColors = function(nums) {
  var redIndex = 0
  var blueIndex = nums.length - 1
  var i = 0
  while (i <= blueIndex) {
    if (nums[i] === 0) {
      swap(nums, i++, redIndex++)
    } else if (nums[i] === 2) {
      swap(nums, i, blueIndex--)
    } else {
      i++
    }
  }
};

var swap = function(nums, i, j) {
  var temp = nums[i]
  nums[i] = nums[j]
  nums[j] = temp
}
```
