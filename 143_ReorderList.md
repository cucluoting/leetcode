# 143. Reorder List

Given a singly linked list L: L0→L1→…→Ln-1→Ln,  
reorder it to: L0→Ln→L1→Ln-1→L2→Ln-2→…

You must do this in-place without altering the nodes' values.

For example,  
Given `{1,2,3,4}`, reorder it to `{1,4,2,3}`.

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {void} Do not return anything, modify head in-place instead.
 */
var reorderList = function(head) {
  var mid = findMid(head)
  var right = reverse(mid)
  var left = head
  while (right && right.next) {
    var target = right
    right = right.next
    target.next = left.next
    left.next = target
    left = left.next.next
  }
};

var findMid = function(head) {
  var slow = head
  var fast = head
  while (fast && fast.next) {
    fast = fast.next
    if (fast.next) fast = fast.next
    slow = slow.next
  }
  return slow
};

var reverse = function(head) {
  var prev = null
  while (head) {
    var next = head.next
    head.next = prev
    prev = head
    head = next
  }
  return prev
};
```
