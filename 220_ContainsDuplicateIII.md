# 220. Contains Duplicate III

Given an array of integers, find out whether there are two distinct indices i and j in the array such that the `absolute` difference between `nums[i]` and `nums[j]` is at most t and the `absolute` difference between i and j is at most k.

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @param {number} t
 * @return {boolean}
 */
var containsNearbyAlmostDuplicate = function(nums, k, t) {
  if (t < 0 || k < 1) return false
  const map = new Map()
  const w = t + 1
  for (let i = 0, len = nums.length; i < len; i++) {
    const num = nums[i]
    const id = Math.floor(num / w)
    console.log(id)
    // |nums[j] - nums[i]| < w
    // 等价于 |nums[j]/w - nums[i]/w| < 1
    if (map.has(id)
      || (map.has(id - 1) && Math.abs(map.get(id - 1) - num) < w)
      || (map.has(id + 1) && Math.abs(map.get(id + 1) - num) < w)) {
      return true
    }
    map.set(id, num)
    // 及时清理元素距离大于k的值
    if (i >= k) {
      map.delete(Math.floor(nums[i - k] / w))
    }
  }
  return false
};
```
