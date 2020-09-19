# 45. Jump Game II

Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Your goal is to reach the last index in the minimum number of jumps.

**Example:**
```
Input: [2,3,1,1,4]
Output: 2
Explanation: The minimum number of jumps to reach the last index is 2.
    Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

**Note:**

You can assume that you can always reach the last index.

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var jump = function(nums) {
  let maxPosition = 0
  let end = 0
  let result = 0
  for (let i = 0; i < nums.length - 1; i++) {
    maxPosition = Math.max(maxPosition, i + nums[i])
    if (i === end) {
      end = maxPosition
      result += 1
    }
  }
  return result
};
```
