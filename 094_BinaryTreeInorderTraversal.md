# 94. Binary Tree Inorder Traversal

Given a binary tree, return the inorder traversal of its nodes' values.

For example:
Given binary tree `[1,null,2,3]`,

```
   1
    \
     2
    /
   3
```

return `[1,3,2]`.

**Note:** Recursive solution is trivial, could you do it iteratively?

迭代：
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
 * @return {number[]}
 */
var inorderTraversal = function(root) {
  var result = []
  var tempArr = []
  while(root || tempArr.length > 0) {
    if (root) {
      tempArr.push(root)
      // 左
      root = root.left
    } else {
      root = tempArr.pop()
      // 中
      result.push(root.val)
      // 右
      root = root.right
    }
  }
  return result
};

```

(递归)
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
 * @return {number[]}
 */
var inorderTraversal = function(root) {
  var result = []
  helper(root, result)
  return result
};

var helper = function(root, result) {
  if (!root) return
  helper(root.left, result)
  result.push(root.val)
  helper(root.right, result)
}
```
