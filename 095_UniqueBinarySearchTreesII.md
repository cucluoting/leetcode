# 95. Unique Binary Search Trees II

Given an integer n, generate all structurally unique **BST's** (binary search trees) that store values 1...n.

For example,  
Given n = 3, your program should return all 5 unique BST's shown below.

```
   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
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
 * @param {number} n
 * @return {TreeNode[]}
 */
var generateTrees = function(n) {
  if (n <= 0) return []
  return helper(1, n)
};

var helper = function(start, end) {
  var result = []
  if (start > end) {
    result.push(null)
    return result
  }
  for (var i = start; i <= end; i++) {
    var left = helper(start, i - 1)
    var right = helper(i + 1, end)
    for (var j = 0; j < left.length; j++) {
      for (var k = 0; k < right.length; k++) {
        var root = new TreeNode(i)
        root.left = left[j]
        root.right = right[k]
        result.push(root)
      }
    }
  }
  return result
}
```
