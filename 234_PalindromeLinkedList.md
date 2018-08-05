# 234. Palindrome Linked List

Given a singly linked list, determine if it is a palindrome.

**Example 1:**
```
Input: 1->2
Output: false
```
**Example 2:**
```
Input: 1->2->2->1
Output: true
```
**Follow up:**  
Could you do it in O(n) time and O(1) space?

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
 * @return {boolean}
 */
var isPalindrome = function(head) {
  if (!head || !head.next) return true
  
  let fast = head
  let slow = head
  while (fast.next && fast.next.next) {
    slow = slow.next
    fast = fast.next.next
  }
  
  const last = slow.next
  let temp = null
  // 翻转后半段链表
  while (last.next) {
    temp = last.next
    last.next = temp.next
    temp.next = slow.next
    slow.next = temp
  }
  
  let prev = head
  while (slow.next) {
    slow = slow.next
    if (prev.val !== slow.val) return false
    prev = prev.next
  }
  return true
};
```
