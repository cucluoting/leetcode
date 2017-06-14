# 24. Swap Nodes in Pairs

Given a linked list, swap every two adjacent nodes and return its head.

For example,
Given `1->2->3->4`, you should return the list as `2->1->4->3`.

Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.

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
var swapPairs = function(head) {
  var fast = head
  var slow = head
  var result = new ListNode(0)
  var temp = result
  while(fast) {
    if(fast.next) {
      fast = fast.next
      temp.next = new ListNode(fast.val)
      temp = temp.next
      temp.next = new ListNode(slow.val)
      temp = temp.next

      slow = slow.next.next
      fast = fast.next
    }else {
      temp.next = fast
      fast = fast.next
    }
  }
  return result.next
};
```
