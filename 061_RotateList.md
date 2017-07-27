# 61. Rotate List

Given a list, rotate the list to the right by k places, where k is non-negative.

For example:  
Given `1->2->3->4->5->NULL` and k = 2,  
return `4->5->1->2->3->NULL`.


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
 * @param {number} k
 * @return {ListNode}
 */
var rotateRight = function(head, k) {
  if (!head || k === 0) return head
  var len = 1
  var temp = head
  while (temp.next) {
    temp = temp.next
    len++
  }
  // 形成环
  temp.next = head

  // k有可能大于head的长度，所以要k%len
  for (var i = 0; i < len - k % len; i++) {
    temp = temp.next
  }
  head = temp.next
  temp.next = null
  return head
};
```
