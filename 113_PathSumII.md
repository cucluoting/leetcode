# 113. Path Sum II

Given a binary tree and a sum, find all root-to-leaf paths where each path's sum equals the given sum.

For example:  
Given the below binary tree and `sum = 22`,

```
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
```

return

```
[
   [5,4,11,2],
   [5,8,4,5]
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
 * @param {number} sum
 * @return {number[][]}
 */
var pathSum = function(root, sum) {
  var result = []
  helper(root, sum, result, [])
  return result
};

var helper = function(root, sum, result, tempItem) {
  if (!root) return
  tempItem.push(root.val)
  if (!root.left && !root.right && (sum - root.val === 0)) {
    result.push(tempItem.slice(0))
  } else {
    helper(root.left, sum - root.val, result, tempItem)
    helper(root.right, sum - root.val, result, tempItem)
  }
  tempItem.pop()
}
```
