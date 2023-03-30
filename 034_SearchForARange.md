# 34. Search for a Range

Given an array of integers sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return `[-1, -1]`.

For example,
Given `[5, 7, 7, 8, 8, 10]` and target value 8,
return `[3, 4]`.


```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var searchRange = function(nums, target) {
  var l = 0
  var r = nums.length - 1
  var begin = -1
  var end = -1
  while (l <= r) {
    var m = Math.floor(r - l)
    if (nums[m] === target) {
      if (nums[m - 1] !== target) {
        begin = m
        break
      } else {
        r = m - 1
      }
    } else if(nums[m] < target) {
      l = m + 1
    } else {
      r = m - 1
    }
  }
  for (var i = begin; i < nums.length; i++) {
    if (nums[i] === target) {
      end = i
    } else {
      break
    }
  }
  return [begin, end]
};
```

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var searchRange = function(nums, target) {
  const result = [-1, -1];
  const start = getFirstPosition(nums, target);
  const end = getFirstPosition(nums, target + 1) - 1;
  if (start < nums.length && nums[start] === target) {
    return [start, end];
  }
  
  return [-1, -1];
};

var getFirstPosition = function(nums, target) {
  let left = 0; 
  let right = nums.length - 1;
  let mid;
  while(left <= right) {
    mid = Math.floor((left + right) / 2);
    if (nums[mid] < target) {
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }
  return left;
}
```
