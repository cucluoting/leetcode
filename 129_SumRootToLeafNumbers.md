# 129. Sum Root to Leaf Numbers

Given a binary tree containing digits from `0-9` only, each root-to-leaf path could represent a number.

An example is the root-to-leaf path `1->2->3` which represents the number `123`.

Find the total sum of all root-to-leaf numbers.

For example,

```
    1
   / \
  2   3
```

The root-to-leaf path `1->2` represents the number `12`.  
The root-to-leaf path `1->3` represents the number `13`.  

Return the sum = 12 + 13 = `25`.  

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
var sumNumbers = function(root) {
  return helper(root, 0)
};

var helper = function(root, sum) {
  if (!root) return 0
  if (!root.left && !root.right) {
    return sum * 10 + root.val
  }
  return helper(root.left, sum * 10 + root.val) + helper(root.right, sum * 10 + root.val)
};
```
