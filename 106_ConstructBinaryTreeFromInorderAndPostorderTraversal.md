# 106. Construct Binary Tree from Inorder and Postorder Traversal

Given inorder and postorder traversal of a tree, construct the binary tree.

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
 * @param {number[]} inorder
 * @param {number[]} postorder
 * @return {TreeNode}
 */
var buildTree = function(inorder, postorder) {
  return helper(inorder, postorder)
};

var helper = function(inorder, postorder) {
  if (postorder.length === 0) return null
  var root = new TreeNode(postorder[postorder.length - 1])
  var index = -1
  for (var i = 0; i < inorder.length; i++) {
    if (inorder[i] === root.val) {
      index = i
      break
    }
  }
  root.left = helper(inorder.slice(0, index), postorder.slice(0, index))
  root.right = helper(inorder.slice(index + 1, inorder.length), postorder.slice(index, postorder.length - 1))
  return root
}
```
