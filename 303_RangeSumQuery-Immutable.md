# 303. Range Sum Query - Immutable

Given an integer array nums, find the sum of the elements between indices i and j (i ≤ j), inclusive.

**Example:**
```
Given nums = [-2, 0, 3, -5, 2, -1]

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3
```
**Note:**

1. You may assume that the array does not change.
2. There are many calls to sumRange function.

```javascript
/**
 * @param {number[]} nums
 */
var NumArray = function(nums) {
  this.nums = nums  
  this.sum = [0]
  for (let i = 0; i < this.nums.length; i++) {
    this.sum[i + 1] = this.sum[i] + this.nums[i]
  }
};

/** 
 * @param {number} i 
 * @param {number} j
 * @return {number}
 */
NumArray.prototype.sumRange = function(i, j) {
  return this.sum[j + 1] - this.sum[i]
};

/** 
 * Your NumArray object will be instantiated and called as such:
 * var obj = new NumArray(nums)
 * var param_1 = obj.sumRange(i,j)
 */
```
