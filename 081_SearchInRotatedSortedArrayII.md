# 81. Search in Rotated Sorted Array II

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., `0 1 2 4 5 6 7` might become `4 5 6 7 0 1 2`).

Write a function to determine if a given target is in the array.

The array may contain duplicates.

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {boolean}
 */
var search = function(nums, target) {
  if (nums.length === 0) return false
  var l = 0
  var r = nums.length - 1
  while (l <= r) {
    var m = Math.floor((r + l) / 2)
    if (nums[m] === target) return true

    // 这种情况下无法判断target在哪一侧
    if (nums[l] === nums[m] && nums[r] === nums[m]) {
      l++
      r--
    } else if (nums[m] >= nums[l]) {
      if (target >= nums[l] && target < nums[m]) {
        r = m - 1
      } else {
        l = m + 1
      }
    } else {
      if (target <= nums[r] && target > nums[m]) {
        l = m + 1
      } else {
        r = m - 1
      }
    }
  }
  return false
};

```
