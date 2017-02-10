# 26. Remove Duplicates from Sorted Array

Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this in place with constant memory.

For example,
Given input array nums = `[1,1,2]`,

Your function should return length = `2`, with the first two elements of nums being 1 and 2 respectively. It doesn't matter what you leave beyond the new length.

这题的重点是在计算长度的时候还要改变原数组。

先记录原数组长度，再从尾到头遍历数组。

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
  if(nums.length === 0) return 0
  var i = nums.length - 2,
      number = 1
  while(i >= 0) {
    if(nums[i] === nums[i + 1]) {
      nums.splice(i, 1)
    }else {
      number++
    }
    i--
  }
  return number
};
```

符合传统编程思想的方法：

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
  if(nums.length === 0) return 0
  var i = 1,
      j = 1
  for(; i < nums.length; i++) {
    if(nums[i] !== nums[i - 1]) {
      nums[j] = nums[i]
      j++
    }
  }
  return j
};
```
