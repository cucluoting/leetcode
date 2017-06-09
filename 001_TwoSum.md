# 1. Two Sum

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution.

**Example:**
```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

无脑的写法

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
  var result = []
  for (var i = nums.length - 1; i > 0; i--) {
    for (var j = i - 1; j >= 0; j--) {
      if(target === nums[i] + nums[j]) {
        result = [j, i]
        return result
      }
    }
  }
}
```

hashmap写法

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
  var left,
      tempObj = {}
  for (var i = nums.length - 1; i >= 0; i--) {
    left = target - nums[i]
    if(left in tempObj) {
      return [i, tempObj[left]]
    }else {
      tempObj[nums[i]] = i
    }
  }
};
```
