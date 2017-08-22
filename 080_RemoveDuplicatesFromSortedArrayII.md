# 80. Remove Duplicates from Sorted Array II

Follow up for "Remove Duplicates":  
What if duplicates are allowed at most twice?

For example,  
Given sorted array nums = `[1,1,1,2,2,3]`,

Your function should return length = `5`, with the first five elements of nums being `1, 1, 2, 2` and `3`. It doesn't matter what you leave beyond the new length.

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
  if (nums.length === 0) return 0
  var j = 1
  var count = 1
  for (var i = 1; i < nums.length; i++) {
    if (nums[i] !== nums[i - 1]) {
      nums[j] = nums[i]
      j++
      count = 1
    } else {
      if (count === 1) {
        nums[j] = nums[i]
        j++
      }
      count++
    }
  }
  return j
};
```
