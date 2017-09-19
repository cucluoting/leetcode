# 98. Validate Binary Search Tree

Given a binary tree, determine if it is a valid binary search tree (BST).

Assume a BST is defined as follows:

- The left subtree of a node contains only nodes with keys **less than** the node's key.
- The right subtree of a node contains only nodes with keys **greater than** the node's key.
- Both the left and right subtrees must also be binary search trees.

**Example 1:**
```
    2
   / \
  1   3
```
Binary tree `[2,1,3]`, return true.

**Example 2:**
```
    1
   / \
  2   3
```
Binary tree `[1,2,3]`, return false.


```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {boolean}
 */
var isValidBST = function(root) {
  return helper(root, Number.MIN_SAFE_INTEGER, Number.MAX_SAFE_INTEGER)
};

var helper = function(root, minVal, maxVal) {
  if (!root) return true
  if (root.val <= minVal || root.val >= maxVal) return false
  return helper(root.left, minVal, root.val) && helper(root.right, root.val, maxVal)
}
```
