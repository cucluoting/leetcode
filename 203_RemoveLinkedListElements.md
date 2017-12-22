# 203. Remove Linked List Elements

Remove all elements from a linked list of integers that have value **val**.

**Example**  
**Given**: 1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6, **val** = 6  
**Return**: 1 --> 2 --> 3 --> 4 --> 5

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
 * @param {number} val
 * @return {ListNode}
 */
var removeElements = function(head, val) {
  var result = new ListNode(0)
  var slow = result
  var fast = head
  while (fast) {
    if (fast.val !== val) {
      slow.next = fast
      slow = slow.next
    }
    fast = fast.next
  }
  if (slow.next && slow.next.val === val) slow.next = null
  return result.next
};
```

改进方法：
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
 * @param {number} val
 * @return {ListNode}
 */
var removeElements = function(head, val) {
  if (!head) return null
  var p = head
  while (p && p.next) {
    if (p.next.val === val) {
      p.next = p.next.next
    } else {
    // 只有值不等于val才能跳到下一个节点，否则会漏掉最后一个节点的值等于val的情况
      p = p.next
    }
  }
  return head.val === val ? head.next : head
};
```
