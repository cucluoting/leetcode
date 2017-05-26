# 21. Merge Two Sorted Lists

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

用js写这题是怪怪的。。。

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
var mergeTwoLists = function(l1, l2) {
  if(!l1) return l2
  if(!l2) return l1
  var newList = []
  if(l1.val < l2.val) {
    newList.push(l1)
    l1 = l1.next
  }else {
    newList.push(l2)
    l2 = l2.next
  }
  while(l1 || l2) {
    if(!l1) {
      newList.push(l2)
      l2 = l2.next
    }else if(!l2) {
      newList.push(l1)
      l1 = l1.next
    }else{
      if(l1.val < l2.val) {
        newList.push(l1)
        l1 = l1.next
      }else {
        newList.push(l2)
        l2 = l2.next
      }
    }
  }
  newList.forEach((item, index, array) => {
    item.next = array[index + 1] || null
  })
  return newList[0]
};
```

还是用递归简单明了！不过runtime多了很多。。。

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
var mergeTwoLists = function(l1, l2) {
  if(!l1) return l2
  if(!l2) return l1
  if(l1.val < l2.val) {
    l1.next = mergeTwoLists(l1.next, l2)
    return l1
  }else {
    l2.next = mergeTwoLists(l1, l2.next)
    return l2
  }
};
```
