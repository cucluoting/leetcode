# 215. Kth Largest Element in an Array

Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.

For example,  
Given `[3,2,1,5,6,4]` and k = 2, return 5.

**Note**:  
You may assume k is always valid, 1 ≤ k ≤ array's length.

快速排序法

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findKthLargest = function(nums, k) {
  return quickSort(nums, 0, nums.length - 1)[k - 1]
};

var quickSort = function(nums, start, end) {
  if (start < end) {
    var p = partition(nums, start, end)
    quickSort(nums, start, p - 1)
    quickSort(nums, p + 1, end)
  }
  return nums
};

var partition = function(nums, start, end) {
  var high = start
  var rand = Math.floor(Math.random() * (end - start)) + start
  swap(nums, rand, end)
  for (var i = start; i < end; i++) {
    if (nums[i] > nums[end]) {
      swap(nums, i, high)
      high++
    }
  }
  swap(nums, high, end)
  return high
};

var swap = function(nums, indexA, indexB) {
  var temp = nums[indexB]
  nums[indexB] = nums[indexA]
  nums[indexA] = temp
};
```
