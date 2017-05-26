# 108. Convert Sorted Array to Binary Search Tree

Given an array where elements are sorted in ascending order, convert it to a height balanced BST.

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {number[]} nums
 * @return {TreeNode}
 */
var sortedArrayToBST = function(nums) {
  if(!nums || nums.length === 0) return null
  return helper(nums, 0, nums.length - 1)
};
var helper = function(nums, start, end) {
  if(start > end) return null
  var mid = Math.floor(start + (end - start) / 2)
  var root = new TreeNode(nums[mid])
  root.left = helper(nums, start, mid - 1)
  root.right = helper(nums, mid + 1, end)
  return root
}
```
