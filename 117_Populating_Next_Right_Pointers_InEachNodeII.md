# 117. Populating Next Right Pointers in Each Node II

Follow up for problem "Populating Next Right Pointers in Each Node".

What if the given tree could be any binary tree? Would your previous solution still work?

**Note:**

- You may only use constant extra space.  
For example,  
Given the following binary tree,

```
         1
       /  \
      2    3
     / \    \
    4   5    7
```

After calling your function, the tree should look like:

```
         1 -> NULL
       /  \
      2 -> 3 -> NULL
     / \    \
    4-> 5 -> 7 -> NULL
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
