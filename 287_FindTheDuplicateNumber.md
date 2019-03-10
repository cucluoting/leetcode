# 287. Find the Duplicate Number

Given an array nums containing n + 1 integers where each integer is between 1 and n (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.

**Example 1:**
```
Input: [1,3,4,2,2]
Output: 2
```
**Example 2:**
```
Input: [3,1,3,4,2]
Output: 3
```
**Note:**

1. You must not modify the array (assume the array is read only).
2. You must use only constant, O(1) extra space.
3. Your runtime complexity should be less than O(n2).
4. There is only one duplicate number in the array, but it could be repeated more than once.

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findDuplicate = function(nums) {
  let tortoise = nums[0]
  let hare = nums[0]
  while (true) {
    tortoise = nums[tortoise]
    hare = nums[nums[hare]]
    if (tortoise === hare) break
  }
  let ptr1 = nums[0]
  let ptr2 = tortoise
  while (ptr1 !== ptr2) {
    ptr1 = nums[ptr1]
    ptr2 = nums[ptr2]
  }
  return ptr1
};
```
