# 209. Minimum Size Subarray Sum

Given an array of **n** positive integers and a positive integer **s**, find the minimal length of a **contiguous** subarray of which the sum **≥ s**. If there isn't one, return 0 instead.

For example, given the array `[2,3,1,2,4,3]` and `s = 7`,
the subarray `[4,3]` has the minimal length under the problem constraint.

**More practice:**  
If you have figured out the O(n) solution, try coding another solution of which the time complexity is O(n log n).

解题思路：构建一个窗口，使窗口内所有元素的和刚好大于等于s，不断移动窗口，更新窗口的最小长度。

```javascript
/**
 * @param {number} s
 * @param {number[]} nums
 * @return {number}
 */
var minSubArrayLen = function(s, nums) {
  var len = nums.length
  var result = Number.MAX_VALUE
  var currentMin = 0
  var currentSum = 0
  var left = 0
  var right = 0
  while (right < len) {
    currentSum = currentSum + nums[right++]
    // 当窗口内的和大于s时进入，即窗口长度的最小值
    while (currentSum >= s) {
      currentMin = right - left
      result = Math.min(currentMin, result)
      // 将窗口向后移动，并减去移动后不包含的值
      currentSum = currentSum - nums[left++]
    }
  }
  return result === Number.MAX_VALUE ? 0 : result
};
```
