# 350. Intersection of Two Arrays II

Given two arrays, write a function to compute their intersection.

**Example 1:**
```
Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2,2]
```
**Example 2:**
```
Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [4,9]
```
**Note:**

- Each element in the result should appear as many times as it shows in both arrays.
- The result can be in any order.

**Follow up:**

- What if the given array is already sorted? How would you optimize your algorithm?
- What if nums1's size is small compared to nums2's size? Which algorithm is better?
- What if elements of nums2 are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?

```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function(nums1, nums2) {
  nums1.sort((a, b) => a - b)
  nums2.sort((a, b) => a - b)
  let index1 = 0
  let index2 = 0
  const result = []
  while (index1 < nums1.length && index2 < nums2.length) {
    if (nums1[index1] === nums2[index2]) {
      result.push(nums1[index1])
      index1 += 1
      index2 += 1
    } else if (nums1[index1] < nums2[index2]) {
      index1 += 1
    } else {
      index2 += 1
    }
  }
  return result
};
```

```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function(nums1, nums2) {
  if (nums1.length > nums2.length) {
    return intersect(nums2, nums1)
  }
  const map = new Map()
  for (let i = 0; i < nums1.length; i++) {
    const num = nums1[i]
    map.set(num, map.has(num) ? map.get(num) + 1 : 1)
  }
  const result = []
  for (let i = 0; i < nums2.length; i++) {
    const num = nums2[i]
    let count = map.get(num)
    if (count > 0) {
      result.push(num)
      map.set(num, --count)
    }
  }
  return result
};
```
