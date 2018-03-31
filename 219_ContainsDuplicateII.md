# 219. Contains Duplicate II

Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that **nums[i] = nums[j]** and the **absolute** difference between i and j is at most k.

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {boolean}
 */
var containsNearbyDuplicate = function(nums, k) {
  const map = {}
  for (let i = 0; i < nums.length; i++) {
    const num = nums[i]
    if (map[num] !== undefined && i - map[num] <= k) return true
    map[num] = i
  }
  return false
};
```
