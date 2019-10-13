# 429. N-ary Tree Level Order Traversal

Given an n-ary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

For example, given a `3-ary` tree:

 ![](https://assets.leetcode.com/uploads/2018/10/12/narytreeexample.png)
 
 We should return its level order traversal:
```
[
     [1],
     [3,2,4],
     [5,6]
]
```


**Note:**

1. The depth of the tree is at most `1000`.
2. The total number of nodes is at most `5000`.

```javascript
/**
 * // Definition for a Node.
 * function Node(val,children) {
 *    this.val = val;
 *    this.children = children;
 * };
 */
/**
 * @param {Node} root
 * @return {number[][]}
 */
var levelOrder = function(root) {
  var result = []
  helper(result, 0, root)
  return result
};
var helper = function(result, level, root) {
  if(!root) return
  if(!result[level]) result[level] = []
  
  result[level].push(root.val)
  
  const children = root.children
  for (let i = 0; i < children.length; i++) {
    helper(result, level + 1, children[i])
  }
}  
```
