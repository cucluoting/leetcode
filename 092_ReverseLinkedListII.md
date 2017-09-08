# 92. Reverse Linked List II

Reverse a linked list from position m to n. Do it in-place and in one-pass.

For example:
Given `1->2->3->4->5->NULL`, m = 2 and n = 4,

return `1->4->3->2->5->NULL`.

**Note:**
Given m, n satisfy the following condition:
1 ≤ m ≤ n ≤ length of list.

😅
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
 * @param {number} m
 * @param {number} n
 * @return {ListNode}
 */
var reverseBetween = function(head, m, n) {
  var left = head
  for (var i = 1; i < m; i++) {
    left = left.next
  }
  while(m < n) {
    var right = left
    for (var i = m; i < n; i++) {
      right = right.next
    }
    var tempVal = left.val
    left.val = right.val
    right.val = tempVal
    left = left.next
    ++m
    --n
  }
  return head
};
```

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
 * @param {number} m
 * @param {number} n
 * @return {ListNode}
 */
var reverseBetween = function(head, m, n) {
  var dummy = new ListNode(0)
  dummy.next = head
  var start = dummy
  for (var i = 1; i < m; i++) {
    start = start.next
  }
  var mPoint = start.next
  for (var i = m; i < n; i++) {
    var temp = mPoint.next
    mPoint.next = temp.next
    temp.next = start.next
    start.next = temp
  }
  return dummy.next
};
```
