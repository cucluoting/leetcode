# 86. Partition List

Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.

You should preserve the original relative order of the nodes in each of the two partitions.

For example,  
Given `1->4->3->2->5->2` and `x = 3`,  
return `1->2->2->4->3->5`.

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
 * @param {number} x
 * @return {ListNode}
 */
var partition = function(head, x) {
  var leftDummy = new ListNode(0)
  var rightDummy = new ListNode(0)
  var leftCur = leftDummy
  var rightCur = rightDummy
  while(head) {
    if (head.val < x) {
      leftCur.next = head
      leftCur = leftCur.next        
    } else {
      rightCur.next = head
      rightCur = rightCur.next
    }
    head = head.next
  }
  rightCur.next = null
  leftCur.next = rightDummy.next
  return leftDummy.next
};
```
