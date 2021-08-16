Given an array of n integers nums, a **132 pattern** is a subsequence of three integers `nums[i]`, `nums[j]` and `nums[k]` such that `i < j < k` and `nums[i] < nums[k] < nums[j]`.

Return true if there is a **132 pattern** in nums, otherwise, return false.

 

**Example 1:**
```
Input: nums = [1,2,3,4]
Output: false
Explanation: There is no 132 pattern in the sequence.
```
**Example 2:**
```
Input: nums = [3,1,4,2]
Output: true
Explanation: There is a 132 pattern in the sequence: [1, 4, 2].
```
**Example 3:**
```
Input: nums = [-1,3,2,0]
Output: true
Explanation: There are three 132 patterns in the sequence: [-1, 3, 2], [-1, 3, 0] and [-1, 2, 0].
```

**Constraints:**
- `n == nums.length`
- `1 <= n <= 2 * 105`
- `-109 <= nums[i] <= 109`


```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var find132pattern = function (nums) {
  const len = nums.length
  const stack = [nums[len - 1]]
  let maxNumK = -Infinity

  for (let i = len - 1; i >= 0; i--) {
    // 1
    if (nums[i] < maxNumK) {
      return true
    }
    while (stack.length && (nums[i] > stack[stack.length - 1])) {
      // 2
      maxNumK = stack[stack.length - 1]
      stack.pop()
    }
    // 3
    if (nums[i] > maxNumK) {
      stack.push(nums[i])
    }
  }
  return false
};
```
