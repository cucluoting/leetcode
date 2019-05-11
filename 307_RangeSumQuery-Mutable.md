# 307. Range Sum Query - Mutable

Given an integer array nums, find the sum of the elements between indices i and j (i ≤ j), inclusive.

The update(i, val) function modifies nums by updating the element at index i to val.

**Example:**
```
Given nums = [1, 3, 5]

sumRange(0, 2) -> 9
update(1, 2)
sumRange(0, 2) -> 8
```
**Note:**

1. The array is only modifiable by the update function.
2. You may assume the number of calls to update and sumRange function is distributed evenly.

```javascript
/**
 * @param {number[]} nums
 */
var NumArray = function(nums) {
  if (nums.length > 0) {
    this.len = nums.length
    this.tree = new Array(this.len * 2)
    this.buildTree(nums)
  }
};

NumArray.prototype.buildTree = function(nums) {
  for (var i = this.len, j = 0; i < 2 * this.len; i++, j++) {
    this.tree[i] = nums[j]
  }
  for (var i = this.len - 1; i > 0; --i) {
    this.tree[i] = this.tree[i * 2] + this.tree[i * 2 + 1]
  }
}

/** 
 * @param {number} i 
 * @param {number} val
 * @return {void}
 */
NumArray.prototype.update = function(i, val) {
  i += this.len
  this.tree[i] = val
  while (i > 0) {
    let left = i
    let right = i
    if (i % 2 === 0) {
      right = i + 1
    } else {
      left = i - 1
    }
    this.tree[Math.floor(i / 2)] = this.tree[left] + this.tree[right]
    i = Math.floor(i / 2)
  }
};

/** 
 * @param {number} i 
 * @param {number} j
 * @return {number}
 */
NumArray.prototype.sumRange = function(i, j) {
  i += this.len
  j += this.len
  let sum = 0
  while (i <= j) {
    if ((i % 2) === 1) {
      sum += this.tree[i]
      i++
    }
    if ((j % 2) === 0) {
      sum += this.tree[j]
      j--
    }
    i = Math.floor(i / 2)
    j = Math.floor(j / 2)
  }
  return sum
};

/** 
 * Your NumArray object will be instantiated and called as such:
 * var obj = new NumArray(nums)
 * obj.update(i,val)
 * var param_2 = obj.sumRange(i,j)
 */
```
