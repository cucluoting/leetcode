# 19. Remove Nth Node From End of List

Given a linked list, remove the n<sup>th</sup> node from the end of list and return its head.

For example,

```
   Given linked list: 1->2->3->4->5, and n = 2.

   After removing the second node from the end, the linked list becomes 1->2->3->5.
```

**Note:**
Given n will always be valid.
Try to do this in one pass.

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
 * @param {number} n
 * @return {ListNode}
 */
var removeNthFromEnd = function(head, n) {
  var length = 0
  var index = 0
  var result = new ListNode(0)
  result.next = head
  var tempNode = head

  while (tempNode) {
    length++
    tempNode = tempNode.next
  }

  tempNode = result
  index = length - n
  for (var i = 0; i < index; i++) {
    tempNode = tempNode.next
  }
  tempNode.next = tempNode.next.next
  
  return result.next
};
```

这个步数差的解法非常厉害。。反正我是想不到。。
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
 * @param {number} n
 * @return {ListNode}
 */
var removeNthFromEnd = function(head, n) {
  var result = new ListNode(0)
  var tempNode = result
  result.next = head

  for (var i = 0; i < n; i++) {
    head = head.next
  }

  while (head) {
    head = head.next
    tempNode = tempNode.next
  }
  
  tempNode.next = tempNode.next.next
  return result.next
};
```
