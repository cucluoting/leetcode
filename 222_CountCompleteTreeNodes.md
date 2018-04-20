# 222. Count Complete Tree Nodes

Given a **complete** binary tree, count the number of nodes.

**Definition of a complete binary tree from [Wikipedia](https://en.wikipedia.org/wiki/Binary_tree#Types_of_binary_trees)**:  
In a complete binary tree every level, except possibly the last, is completely filled, and all nodes in the last level are as far left as possible. It can have between 1 and 2<sup>h</sup> nodes inclusive at the last level h.

完全二叉树

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
 * @return {number}
 */
var countNodes = function(root) {
  let leftHeight = traverse(root, 'left')
  let rightHeight = traverse(root, 'right')
  
  if (leftHeight === rightHeight) return Math.pow(2, leftHeight) - 1
  return countNodes(root.left) + countNodes(root.right) + 1
};

var traverse = function(root, type) {
  let height = 0
  let currNode = root
  while (currNode) {
    height++
    currNode = currNode[type]
  }
  return height
};
```
