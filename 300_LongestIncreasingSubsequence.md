# 300. Longest Increasing Subsequence

Given an unsorted array of integers, find the length of longest increasing subsequence.

**Example:**
```
Input: [10,9,2,5,3,7,101,18]
Output: 4 
Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4. 
```
**Note:**

- There may be more than one LIS combination, it is only necessary for you to return the length.
- Your algorithm should run in O(n2) complexity.

**Follow up:** Could you improve it to O(n log n) time complexity?


```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var lengthOfLIS = function(nums) {
  if (nums.length === 0) {
    return 0
  }
  let result = 1
  const dp = new Array(nums.length)
  dp[0] = 1
  for (let i = 1; i < nums.length; i++) {
    let maxVal = 0
    for (let j = 0; j < i; j++) {
      if (nums[i] > nums[j]) {
        maxVal = Math.max(maxVal, dp[j])
      }
    }
    dp[i] = maxVal + 1
    result = Math.max(result, dp[i])
  }
  return result
};
```
