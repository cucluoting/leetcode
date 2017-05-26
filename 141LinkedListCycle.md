# 141. Linked List Cycle

Given a linked list, determine if it has a cycle in it.

Follow up:  
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
 * @return {boolean}
 */
var hasCycle = function(head) {
  if(!head) return false
  var slow = head
  var fast = head
  while(fast.next && fast.next.next) {
    slow = slow.next
    fast = fast.next.next
    if(slow === fast) {
      return true
    }
  }
  return false
};
```
