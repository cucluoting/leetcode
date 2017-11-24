# 153. Find Minimum in Rotated Sorted Array

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., `0 1 2 4 5 6 7` might become `4 5 6 7 0 1 2`).

Find the minimum element.

You may assume no duplicate exists in the array.

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMin = function(nums) {
  var left = 0
  var right = nums.length - 1

  while (left < right) {
    var mid = Math.floor((right - left) / 2 + left)
    if (nums[mid] < nums[right]) {
      right = mid
    } else {
      left = mid + 1
    }
  }
  
  return nums[left]
};
```
