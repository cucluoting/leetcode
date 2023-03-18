# 378. Kth Smallest Element in a Sorted Matrix

Given an n x n matrix where each of the rows and columns is sorted in ascending order, return the kth smallest element in the matrix.

Note that it is the kth smallest element **in the sorted order**, not the kth **distinct** element.

You must find a solution with a memory complexity better than O(n2).

**Example 1:**
```
Input: matrix = [[1,5,9],[10,11,13],[12,13,15]], k = 8
Output: 13
Explanation: The elements in the matrix are [1,5,9,10,11,12,13,13,15], and the 8th smallest number is 13
```
**Example 2:**
```
Input: matrix = [[-5]], k = 1
Output: -5
```

**Constraints:**

- `n == matrix.length == matrix[i].length`
- `1 <= n <= 300`
- `-109 <= matrix[i][j] <= 109`
- All the rows and columns of matrix are **guaranteed** to be sorted in **non-decreasing order**.
- `1 <= k <= n2`
 

**Follow up:**

- Could you solve the problem with a constant memory (i.e., O(1) memory complexity)?
- Could you solve the problem in O(n) time complexity? The solution may be too advanced for an interview but you may find reading this paper fun.

```javascript
/**
 * @param {number[][]} matrix
 * @param {number} k
 * @return {number}
 */
var kthSmallest = function (matrix, k) {
  const n = matrix.length
  let left = matrix[0][0]
  let right = matrix[n - 1][n - 1]
  while (left < right) {
    let mid = left + ((right - left) >> 1)
    if (helper(matrix, n, mid) < k) {
      left = mid + 1
    } else {
      right = mid
    }
  }
  return left
};

/**
 * 计算 matrix 中不比 mid 大的数量
 */
var helper = function (matrix, n, mid) {
  let row = n - 1
  let column = 0
  let count = 0
  while (row >= 0 && column < n) {
    if (matrix[row][column] <= mid) {
      count += row + 1
      column += 1
    } else {
      row -= 1
    }
  }
  return count
}
```