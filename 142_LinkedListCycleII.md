# 142. Linked List Cycle II

Given a linked list, return the node where the cycle begins. If there is no cycle, return `null`.

**Note:** Do not modify the linked list.

**Follow up:**
Can you solve it without using extra space?

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
 * @return {ListNode}
 */
var detectCycle = function(head) {
  if (!head) return null
  var slow = head
  var fast = head
  while (fast.next && fast.next.next) {
    slow = slow.next
    fast = fast.next.next
    if (slow === fast) {
      slow = head
      while (slow !== fast) {
        fast = fast.next
        slow = slow.next
      }
      return slow
    }
  }
  return null
};
```
