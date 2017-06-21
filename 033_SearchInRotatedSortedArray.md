# 33. Search in Rotated Sorted Array

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., `0 1 2 4 5 6 7` might become `4 5 6 7 0 1 2`).

You are given a target value to search. If found in the array return its index, otherwise return -1.

You may assume no duplicate exists in the array.


```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var search = function(nums, target) {
  var l = 0
  var r = nums.length - 1
  while (l <= r) {
    var m = Math.ceil(r - l)
    if (nums[m] === target){
      return m
    }

    if (nums[m] > nums[l]) {
      if (target < nums[m] && target >= nums[l]) {
        r = m - 1
      }else {
        l = m + 1
      }
    }else {
      if (target > nums[m] && target <= nums[r]) {
        l = m + 1
      }else {
        r = m - 1
      }
    }
  }
  return -1
};
```
