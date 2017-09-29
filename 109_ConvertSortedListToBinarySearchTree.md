# 109. Convert Sorted List to Binary Search Tree

Given a singly linked list where elements are sorted in ascending order, convert it to a height balanced BST.

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {TreeNode}
 */
var sortedListToBST = function(head) {
  return helper(head, null)
};

var helper = function(start, end) {
  if (start === end) return null
  var slow = start
  var fast = start
  while(fast !== end && fast.next !== end) {
    slow = slow.next
    fast = fast.next.next
  }
  var root = new TreeNode(slow.val)
  root.left = helper(start, slow)
  root.right = helper(slow.next, end)
  return root
}
```
