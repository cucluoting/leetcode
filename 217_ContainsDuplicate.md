# 217. Contains Duplicate

Given an array of integers, find if the array contains any duplicates. Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

没有追求的解法：

```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
  if (nums.length < 2) return false
  nums = nums.sort()
  for (var i = 1; i < nums.length; i++) {
    if (nums[i] === nums[i - 1]) return true
  }
  return false
};
```

巧妙的解法：

```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
  return nums.length !== new Set(nums).size
};
```
