# 138. Copy List with Random Pointer

A linked list is given such that each node contains an additional random pointer which could point to any node in the list or null.

Return a deep copy of the list.

```javascript
/**
 * Definition for singly-linked list with a random pointer.
 * function RandomListNode(label) {
 *     this.label = label;
 *     this.next = this.random = null;
 * }
 */

/**
 * @param {RandomListNode} head
 * @return {RandomListNode}
 */
var copyRandomList = function(head) {
  if (!head) return null
  var h = head
  var n = null
  while (h) {
    var node = new RandomListNode(h.label)
    node.random = h.random
    n = h.next
    h.next = node
    node.next = n
    h = n
  }
  h = head.next
  while(h) {
    if (h.random) h.random = h.random.next
    if (!h.next) break
    h = h.next.next
  }
  h = head
  var dummy = new RandomListNode(0)
  var p = dummy
  while(h) {
    p.next = h.next
    p = p.next
    h.next = h.next.next
    h = h.next
  }
  return dummy.next
};
```
