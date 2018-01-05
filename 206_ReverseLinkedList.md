# 206. Reverse Linked List

Reverse a singly linked list.

**Hint:**  
A linked list can be reversed either iteratively or recursively. Could you implement both?

迭代法
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
var reverseList = function(head) {
  var prev = null
  var curr = head
  while (curr) {
    // 先保存next节点
    var next = curr.next
    // 将当前节点的next指向之前的节点以实现翻转
    curr.next = prev
    // 更新prev为添加当前节点后的翻转链表
    prev = curr
    
    curr = next
  }
  return prev
};
```

递归法
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
var reverseList = function(head) {
  if (!head || !head.next) return head
  var temp = head
  // head是后一个节点
  head = reverseList(temp.next)
  // 因为temp是head的前一个节点, 所以相当于将当前节点加到head后
  temp.next.next = temp
  // 将temp即现在head的最后一个节点的next置空
  temp.next = null
  return head
};
```
