# 437. Path Sum III

You are given a binary tree in which each node contains an integer value.

Find the number of paths that sum to a given value.

The path does not need to start or end at the root or a leaf, but it must go downwards (traveling only from parent nodes to child nodes).

The tree has no more than 1,000 nodes and the values are in the range -1,000,000 to 1,000,000.

**Example:**

```
root = [10,5,-3,3,2,null,11,3,-2,null,1], sum = 8

      10
     /  \
    5   -3
   / \    \
  3   2   11
 / \   \
3  -2   1

Return 3. The paths that sum to 8 are:

1.  5 -> 3
2.  5 -> 2 -> 1
3. -3 -> 11
```

解题思路：深度优先法，不断的更新临时索引路径，每添加一个节点就往前寻找是否有等于结果的目标路径。**注意：可能有节点为0或者负数**

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
 * @return {number}
 */
var pathSum = function(root, sum) {
  return dfs(root, sum, [])
};

var dfs = function(node, sum, path) {
  if (!node) {
    return 0
  }
  path.push(node.val)
  let result = 0
  let tempSum = 0
  for (let i = path.length - 1; i >= 0; i--) {
    tempSum += path[i];
    if (tempSum === sum) {
      result += 1
    }
  }
  result += dfs(node.left, sum, path)
  result += dfs(node.right, sum, path)
  path.pop()
  return result
}
```
