# 662. Maximum Width of Binary Tree
Given the root of a binary tree, return the maximum width of the given tree.

The maximum width of a tree is the maximum width among all levels.

The width of one level is defined as the length between the end-nodes (the leftmost and rightmost non-null nodes), where the null nodes between the end-nodes that would be present in a complete binary tree extending down to that level are also counted into the length calculation.

It is guaranteed that the answer will in the range of a 32-bit signed integer.

 

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/05/03/width1-tree.jpg)
```
Input: root = [1,3,2,5,3,null,9]
Output: 4
Explanation: The maximum width exists in the third level with length 4 (5,3,null,9).
```

**Example 2:**

![](https://assets.leetcode.com/uploads/2022/03/14/maximum-width-of-binary-tree-v3.jpg)
```
Input: root = [1,3,2,5,null,null,9,6,null,7]
Output: 7
Explanation: The maximum width exists in the fourth level with length 7 (6,null,null,null,null,null,7).
```

**Example 3:**

![](https://assets.leetcode.com/uploads/2021/05/03/width3-tree.jpg)
```
Input: root = [1,3,2,5]
Output: 2
Explanation: The maximum width exists in the second level with length 2 (3,2).
```

**Constraints:**

- The number of nodes in the tree is in the range `[1, 3000]`.
- `-100 <= Node.val <= 100`

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
const widthOfBinaryTree = function (root) {
  let maxWidth = 0;
  const minIndex = [];

  var dfs = function (node, depth, index) {
    if (node === null) {
      return;
    }
    // 设置当前层的最开始位置
    if (minIndex[depth] === undefined) {
      minIndex.push(index);
    }

    // 当前位置和当前层最开始位置的距离
    const newIndex = index - minIndex[depth];

    maxWidth = Math.max(newIndex + 1, maxWidth);

    dfs(node.left, depth + 1, 2 * newIndex);
    dfs(node.right, depth + 1, 2 * newIndex + 1);
  };

  dfs(root, 0, 0);
  return maxWidth;
};

```
