# 169. Majority Element

Given an array of size n, find the majority element. The majority element is the element that appears **more than** `⌊ n/2 ⌋` times.

You may assume that the array is non-empty and the majority element always exist in the array.


[众数](https://zh.wikipedia.org/wiki/%E4%BC%97%E6%95%B0_(%E6%95%B0%E5%AD%A6))

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
  nums.sort()
  return nums[Math.floor(nums.length / 2)]
};
```

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
  var candidate = 0
  var count = 0
  for (var i = 0; i < nums.length; i++) {
    if(count === 0) {
      candidate = nums[i]
      count++
    }else {
      if(candidate === nums[i]) {
        count++
      }else {
        count--
      }
    }
  }
  return candidate
};
```
