# 82. Remove Duplicates from Sorted List II

Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list.

For example,  
Given `1->2->3->3->4->4->5`, return `1->2->5`.  
Given `1->1->1->2->3`, return `2->3`.


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
  var dummy = new ListNode(0)
  dummy.next = head
  var prevItem = dummy
  var item = head
  while (item) {
    while(item.next && prevItem.next.val === item.next.val) {
      // 若出现重复节点，将item移动到最后一个值相同的节点以便进一步判断
      item = item.next
    }
    if (prevItem.next === item) {
      // 正常往前移动
      prevItem = prevItem.next
    } else {
      // 若出现值相同的节点，直接跳过
      prevItem.next = item.next
    }
    item = item.next
  }
  return dummy.next
};
```
