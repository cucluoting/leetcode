# 2. Add Two Numbers

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Input:** (2 -> 4 -> 3) + (5 -> 6 -> 4)

**Output:** 7 -> 0 -> 8

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function(l1, l2) {
  var tempNum = 0
  var result = new ListNode(0)
  var pointer = result
  while(l1 || l2) {
    if(l1) {
      pointer.next = l1
      pointer = pointer.next
      l1 = l1.next
      pointer.val += tempNum
      if(l2) {
        pointer.val += l2.val
        l2 = l2.next
      }
    }else if(l2) {
      pointer.next = l2
      pointer = pointer.next
      l2 = l2.next
      pointer.val += tempNum
    }
    if(pointer.val > 9) {
      pointer.val -= 10
      tempNum = 1
    }else {
      tempNum = 0
    }
  }
  if(tempNum > 0) pointer.next = { val: tempNum, next: null }
  return result.next
};
```

改进版

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function(l1, l2) {
  var tempNum = 0
  var result = new ListNode(0)
  var pointer = result
  while(l1 || l2) {
    var val1 = l1 ? l1.val : 0
    var val2 = l2 ? l2.val : 0
    var val = val1 + val2 + tempNum
    if(l1) l1 = l1.next
    if(l2) l2 = l2.next

    pointer.next = new ListNode(tempNum)
    pointer = pointer.next

    tempNum = Math.floor(val / 10)
    pointer.val = val % 10
  }
  if(tempNum > 0) pointer.next = { val: tempNum, next: null }
  return result.next
};
```
