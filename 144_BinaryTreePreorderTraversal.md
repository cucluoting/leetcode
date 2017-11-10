# 144. Binary Tree Preorder Traversal

Given a binary tree, return the preorder traversal of its nodes' values.

For example:  
Given binary tree `[1,null,2,3]`,

```
   1
    \
     2
    /
   3
```

return `[1,2,3]`.

**Note:** Recursive solution is trivial, could you do it iteratively?

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
var preorderTraversal = function(root) {
  var result = []
  var tempArr = root ? [root] : []
  while(tempArr.length) {
    var curr = tempArr.pop()
    result.push(curr.val)
    if (curr.right) {
      tempArr.push(curr.right)
    }
    if (curr.left) {
      tempArr.push(curr.left)
    }
  }
  return result
};

```
