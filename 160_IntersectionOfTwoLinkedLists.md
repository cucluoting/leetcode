# 160. Intersection of Two Linked Lists

Write a program to find the node at which the intersection of two singly linked lists begins.


For example, the following two linked lists:

```
A:          a1 → a2
                   ↘
                     c1 → c2 → c3
                   ↗            
B:     b1 → b2 → b3
```

begin to intersect at node c1.


**Notes:**

- If the two linked lists have no intersection at all, return `null`.
- The linked lists must retain their original structure after the function returns.
- You may assume there are no cycles anywhere in the entire linked structure.
- Your code should preferably run in O(n) time and use only O(1) memory.

**Credits:**
Special thanks to @stellari for adding this problem and creating all test cases.

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */

/**
 * @param {ListNode} headA
 * @param {ListNode} headB
 * @return {ListNode}
 */
var getIntersectionNode = function(headA, headB) {
  if(!headA || !headB) return null
  var lenA = 1
  var lenB = 1
  var tempA = headA
  var tempB = headB
  while(tempA.next) {
    tempA = tempA.next
    lenA++
  }
  while(tempB.next) {
    tempB = tempB.next
    lenB++
  }
  if(tempA.val !== tempB.val) {
    return null
  }
  tempA = headA
  tempB = headB
  if(lenA > lenB) {
    for(var i = 0, len = lenA - lenB; i < len; i++) {
      tempA = tempA.next
    }
  }else if(lenA < lenB) {
    for(var i = 0, len = lenB - lenA; i < len; i++) {
      tempB = tempB.next
    }
  }
  while(tempA.val !== tempB.val) {
    tempA = tempA.next
    tempB = tempB.next
  }
  return tempA
};
```
