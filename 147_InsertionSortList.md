# 147. Insertion Sort List

Sort a linked list using insertion sort.

(插入排序)

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
var insertionSortList = function(head) {
  var result = new ListNode(0)
  var cur = result
  while (head) {
    var next = head.next
    cur = result
    while(cur.next && cur.next.val <= head.val) {
      cur = cur.next
    }
    head.next = cur.next
    cur.next = head
    head = next
  }
  return result.next
};
```
