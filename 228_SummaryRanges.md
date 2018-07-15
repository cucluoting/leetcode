# 228. Summary Ranges

Given a sorted integer array without duplicates, return the summary of its ranges.

**Example 1:**
```
Input:  [0,1,2,4,5,7]
Output: ["0->2","4->5","7"]
Explanation: 0,1,2 form a continuous range; 4,5 form a continuous range.
```

**Example 2:**
```
Input:  [0,2,3,4,6,8,9]
Output: ["0","2->4","6","8->9"]
Explanation: 2,3,4 form a continuous range; 8,9 form a continuous range.
```

```javascript
/**
 * @param {number[]} nums
 * @return {string[]}
 */
var summaryRanges = function(nums) {
  const len = nums.length
  if (len === 0) return nums

  const result = []
  let startIndex = 0
  for (let i = 0; i < len; i++) {
    if (nums[i] !== nums[startIndex] + (i - startIndex)) {
      helper(result, nums[startIndex], nums[i - 1])
      startIndex = i
    }
  }
  helper(result, nums[startIndex], nums[len - 1])
  return result
};

var helper = function(result, left, right) {
  if (left === right) {
    result.push(`${right}`)
  } else {
    result.push(`${left}->${right}`)
  }
}
```
