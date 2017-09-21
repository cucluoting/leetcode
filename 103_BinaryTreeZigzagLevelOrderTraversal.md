# 103. Binary Tree Zigzag Level Order Traversal

Given a binary tree, return the zigzag level order traversal of its nodes' values. (ie, from left to right, then right to left for the next level and alternate between).

For example:
Given binary tree `[3,9,20,null,null,15,7]`,

```
    3
   / \
  9  20
    /  \
   15   7
```

return its zigzag level order traversal as:

```
[
  [3],
  [20,9],
  [15,7]
]
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
 * @return {number[][]}
 */
var zigzagLevelOrder = function(root) {
  var result = []
  helper(root, result, 0)
  result.forEach(function(item, index) {
    if (index % 2) item.reverse()
  })
  return result
};

var helper = function(root, result, index) {
  if (!root) return

  if (!result[index]) result[index] = []
  result[index].push(root.val)
  helper(root.left, result, index + 1)
  helper(root.right, result, index + 1)
}
```
