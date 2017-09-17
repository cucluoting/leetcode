# 96. Unique Binary Search Trees

Given n, how many structurally unique **BST's** (binary search trees) that store values 1...n?

For example,
Given n = 3, there are a total of 5 unique BST's.

```
   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
```

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var numTrees = function(n) {
  var numArr = []
  numArr[0] = 1
  numArr[1] = 1
  for (var i = 2; i <= n; i++) {
    numArr[i] = 0
    for (var j = 0; j <= i - 1; j++) {
      // 左子树 * 右子树
      numArr[i] += numArr[j] * numArr[i - j - 1]
    }
  }
  return numArr[n]
};
```
