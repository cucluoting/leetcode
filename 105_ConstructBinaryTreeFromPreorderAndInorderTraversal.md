# 105. Construct Binary Tree from Preorder and Inorder Traversal

Given preorder and inorder traversal of a tree, construct the binary tree.

**Note:**

You may assume that duplicates do not exist in the tree.

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {number[]} preorder
 * @param {number[]} inorder
 * @return {TreeNode}
 */
var buildTree = function(preorder, inorder) {
  return helper(preorder, inorder)
};

var helper = function(preorder, inorder) {
  if (preorder.length === 0) return null
  var root = new TreeNode(preorder[0])
  var index = -1
  for (var i = 0; i < inorder.length; i++) {
    if (inorder[i] === root.val) {
      index = i
      break
    }
  }
  root.left = helper(preorder.slice(1, index + 1), inorder.slice(0, index))
  root.right = helper(preorder.slice(index + 1, preorder.length), inorder.slice(index + 1, inorder.length))
  return root
}
```
