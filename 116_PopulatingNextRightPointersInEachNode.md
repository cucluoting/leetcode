# 116. Populating Next Right Pointers in Each Node

Given a binary tree

```
    struct TreeLinkNode {
      TreeLinkNode *left;
      TreeLinkNode *right;
      TreeLinkNode *next;
    }
```

Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to `NULL`.

Initially, all next pointers are set to `NULL`.

**Note:**

You may only use constant extra space.  
You may assume that it is a perfect binary tree (ie, all leaves are at the same level, and every parent has two children).

For example,  
Given the following perfect binary tree,

```
         1
       /  \
      2    3
     / \  / \
    4  5  6  7
```

After calling your function, the tree should look like:

```
         1 -> NULL
       /  \
      2 -> 3 -> NULL
     / \  / \
    4->5->6->7 -> NULL
```

```javascript
/**
 * Definition for binary tree with next pointer.
 * function TreeLinkNode(val) {
 *     this.val = val;
 *     this.left = this.right = this.next = null;
 * }
 */

/**
 * @param {TreeLinkNode} root
 * @return {void} Do not return anything, modify tree in-place instead.
 */
var connect = function(root) {
  while (root) {

    var p = root
    var curr = null
    var next = null
    
    while (p) {
      if (p.left) {
        if (curr) curr.next = p.left
        curr = p.left
      }
      if (p.right) {
        if (curr) curr.next = p.right
        curr = p.right
      }
      // 初始化下一层的第一个节点，每层只执行一次
      if (!next) next = p.left ? p.left : p.right
      // 遍历next节点的字节点
      p = p.next
    }
    // 将root指向下一层的第一个节点
    root = next
  }
};

```
(⬇️不符合题意的解法
```javascript
/**
 * Definition for binary tree with next pointer.
 * function TreeLinkNode(val) {
 *     this.val = val;
 *     this.left = this.right = this.next = null;
 * }
 */

/**
 * @param {TreeLinkNode} root
 * @return {void} Do not return anything, modify tree in-place instead.
 */
var connect = function(root) {
  helper(root, [], 0)
};

var helper = function(root, tempArr, level) {
  if (!root) return
  if (tempArr[level]) tempArr[level].next = root
  tempArr[level] = root
  helper(root.left, tempArr, level + 1)
  helper(root.right, tempArr, level + 1)
}
```
