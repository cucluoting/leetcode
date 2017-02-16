# 35. Search Insert Position

Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

Here are few examples.

`[1,3,5,6]`, 5 → 2  
`[1,3,5,6]`, 2 → 1  
`[1,3,5,6]`, 7 → 4  
`[1,3,5,6]`, 0 → 0  

......是我

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var searchInsert = function(nums, target) {
  for(var i = 0, len = nums.length; i < len; i++) {
    if(nums[i] >= target) {
      return i
    }
  }
  return nums.length
};
```

传说中的二分法

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var searchInsert = function(nums, target) {
  var low = 0,
      high = nums.length - 1
  while(low <= high) {
    var mid = Math.ceil((high - low) / 2 + low)
    if(nums[mid] === target) {
      return mid
    }else if(nums[mid] > target) {
      high = mid - 1
    }else {
      low = mid + 1
    }
  }
  return low
};
```
