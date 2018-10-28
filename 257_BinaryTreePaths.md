# 257. Binary Tree Paths

Given a binary tree, return all root-to-leaf paths.

**Note:** A leaf is a node with no children.

**Example:**
```
Input:

   1
 /   \
2     3
 \
  5

Output: ["1->2->5", "1->3"]

Explanation: All root-to-leaf paths are: 1->2->5, 1->3
```

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
 * @return {string[]}
 */
var binaryTreePaths = function(root) {
  const res = []
  if (!root) return res
  if (!root.left && !root.right) {
    res.push(`${root.val}`)
  }
  if (root.left) {
    binaryTreePaths(root.left).forEach((item) => {
      res.push(`${root.val}->${item}`)
    })
  }
  if (root.right) {
    binaryTreePaths(root.right).forEach((item) => {
      res.push(`${root.val}->${item}`)
    })
  }
  return res
};
```
