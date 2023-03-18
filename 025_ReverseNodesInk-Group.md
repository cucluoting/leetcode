# 25. Reverse Nodes in k-Group
Given the head of a linked list, reverse the nodes of the list k at a time, and return the modified list.

k is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of k then left-out nodes, in the end, should remain as it is.

You may not alter the values in the list's nodes, only nodes themselves may be changed.

 

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/10/03/reverse_ex1.jpg)
```
Input: head = [1,2,3,4,5], k = 2
Output: [2,1,4,3,5]
```

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/10/03/reverse_ex2.jpg)
```
Input: head = [1,2,3,4,5], k = 3
Output: [3,2,1,4,5]
```

**Constraints:**

- The number of nodes in the list is n.
- `1 <= k <= n <= 5000`
- `0 <= Node.val <= 1000`

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} k
 * @return {ListNode}
 */
var reverseKGroup = function(head, k) {
  if (!head) {
    return null
  }
  let curr = head
  for (let i = 1; i < k; i++) {
    curr = curr.next
    if (!curr) {
      // 不需要反转
      return head
    }
  }
  let next = curr.next
  // 切割子链表
  curr.next = null
  reverse(head)
  // 串联反转过的链表
  head.next = reverseKGroup(next, k)
  return curr
};

var reverse = function(curr) {
  let prev = null
  while (curr) {
    const next = curr.next
    curr.next = prev
    prev = curr
    curr = next
  }
}
```
