# 110. Balanced Binary Tree

Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.


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
var isBalanced = function(root) {
  return helper(root) >= 0
};

var helper = function(root) {
  if(!root) return 0
  var left = helper(root.left)
  var right = helper(root.right)
  if(left < 0 || right < 0 || Math.abs(left - right) > 1) return -1
  return Math.max(left, right) + 1
}
```
