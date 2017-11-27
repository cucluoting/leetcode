# 162. Find Peak Element

A peak element is an element that is greater than its neighbors.

Given an input array where `num[i] ≠ num[i+1]`, find a peak element and return its index.

The array may contain multiple peaks, in that case return the index to any one of the peaks is fine.

You may imagine that `num[-1] = num[n] = -∞`.

For example, in array `[1, 2, 3, 1]`, 3 is a peak element and your function should return the index number 2.

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findPeakElement = function(nums) {
  var left = 0
  var right = nums.length - 1
  while (left <= right) {
    if (left === right) return left
    var mid = Math.floor((right - left) / 2 + left)
    if (nums[mid] < nums[mid + 1]) {
      left = mid + 1
    } else {
      right = mid
    }
  }
};
```
