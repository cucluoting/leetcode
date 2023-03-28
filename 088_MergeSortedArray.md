# 88. Merge Sorted Array

Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

**Note:**
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2. The number of elements initialized in nums1 and nums2 are m and n respectively.

```javascript
/**
 * @param {number[]} nums1
 * @param {number} m
 * @param {number[]} nums2
 * @param {number} n
 * @return {void} Do not return anything, modify nums1 in-place instead.
 */
var merge = function(nums1, m, nums2, n) {
  if(n === 0) return

  var index1 = m - 1,
      index2 = n - 1,
      i = m + n - 1

  while(index1 >= 0 && index2 >= 0) {
    if(nums1[index1] > nums2[index2]) {
      nums1[i--] = nums1[index1--]
    }else {
      nums1[i--] = nums2[index2--]
    }
  }

  while(index2 >= 0) {
    nums1[i--] = nums2[index2--]
  }
};
```

```javascript
/**
 * @param {number[]} nums1
 * @param {number} m
 * @param {number[]} nums2
 * @param {number} n
 * @return {void} Do not return anything, modify nums1 in-place instead.
 */
var merge = function(nums1, m, nums2, n) {
  while (n > 0) {
    if (nums1[m - 1] > nums2[n - 1]) {
      nums1[m + n - 1] = nums1[m - 1];
      m -= 1;
    } else {
      nums1[m + n - 1] = nums2[n - 1];
      n -= 1;
    }
  }
};
```
