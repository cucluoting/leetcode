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
    // 一直分解数组直到数组不能再分解为之
    var p = partition(nums, start, end)
    quickSort(nums, start, p - 1)
    quickSort(nums, p + 1, end)
  }
  return nums
};

var partition = function(nums, start, end) {
  var high = start
  // 随机从数组中选择一个元素
  var rand = Math.floor(Math.random() * (end - start)) + start
  var x = nums[rand]
  // 先将该元素放到最后，方便与其他元素做比较
  swap(nums, rand, end)
  for (var i = start; i < end; i++) {
    if (nums[i] > x) {
      // 将比x大的元素都放到数组的前面
      swap(nums, i, high)
      high++
    }
  }
  // 使得比x大的元素都在x前面
  swap(nums, high, end)
  // 将数组分成前面是比x大的元素，后面是比x小的元素
  return high
};

var swap = function(nums, indexA, indexB) {
  var temp = nums[indexB]
  nums[indexB] = nums[indexA]
  nums[indexA] = temp
};
```
