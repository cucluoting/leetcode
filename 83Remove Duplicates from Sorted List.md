# 83. Remove Duplicates from Sorted List

Given a sorted linked list, delete all duplicates such that each element appear only once.

For example,  
Given `1->1->2`, return `1->2`.  
Given `1->1->2->3->3`, return `1->2->3`.  

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
var deleteDuplicates = function(head) {
  var item = head
  while(item && item.next) {
    if(item.next.val === item.val) {
      item.next = item.next.next
    }else {
      item = item.next
    }
  }
  return head
};
```
