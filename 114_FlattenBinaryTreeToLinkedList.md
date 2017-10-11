# 114. Flatten Binary Tree to Linked List

Given a binary tree, flatten it to a linked list in-place.

For example,  
Given
```
         1
        / \
       2   5
      / \   \
     3   4   6
```

The flattened tree should look like:

```
   1
    \
     2
      \
       3
        \
         4
          \
           5
            \
             6
```

思路就是不断把右节点换成左节点，并把左节点置空。

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
 * @return {void} Do not return anything, modify root in-place instead.
 */
var flatten = function(root) {
  if (!root) return
  var temp = root.right
  if (root.left) {
    var tail = root.left
    while (tail.right) {
      tail = tail.right
    }
    tail.right = temp
    root.right = root.left
    root.left = null
  }
  flatten(root.right)
};
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
 * @return {void} Do not return anything, modify root in-place instead.
 */
var flatten = function(root) {
  helper(root, null)
};

var helper = function(root, temp) {
  if (!root) return temp
  root.right = helper(root.left, helper(root.right, temp))
  root.left = null
  return root
};
```
