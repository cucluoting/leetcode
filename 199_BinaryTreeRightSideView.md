# 199. Binary Tree Right Side View

Given a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.

For example:  
Given the following binary tree,

```
   1            <---
 /   \
2     3         <---
 \     \
  5     4       <---
```
You should return `[1, 3, 4]`.

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
var rightSideView = function(root) {
  var result = []
  if (!root) return result
  var tempArr = [root]
  var len = tempArr.length
  while (len) {
    // 先存入上一层的最右节点的值
    result.push(tempArr[len - 1].val)
    for (var i = 0; i < len; i++) {
      // 将上一层节点的左右节点提取出来，并删除该节点，构造该层的节点数组
      var node = tempArr.shift()
      if (node.left) tempArr.push(node.left)
      if (node.right) tempArr.push(node.right)
    }
    len = tempArr.length
  }
  return result
};
```
