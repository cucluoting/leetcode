# 148. Sort List

Sort a linked list in O(n log n) time using constant space complexity.

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
var sortList = function(head) {
  if (!head || !head.next) return head
  var slow = head
  var fast = head
  while (fast.next && fast.next.next) {
    slow = slow.next
    fast = fast.next.next
  }
  fast = slow.next
  slow.next = null
  return merge(sortList(head), sortList(fast))
};

var merge = function(list1, list2) {
  var dummy = new ListNode(0)
  var cur = dummy
  while (list1 && list2) {
    if (list1.val < list2.val) {
      cur.next = list1
      list1 = list1.next
    } else {
      cur.next = list2
      list2 = list2.next
    }
    cur = cur.next
  }
  if (list1) cur.next = list1
  if (list2) cur.next = list2
  return dummy.next
};
```
