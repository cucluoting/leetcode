# 16. 3Sum Closest

Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target. Return the sum of the three integers. You may assume that each input would have exactly one solution.

```
    For example, given array S = {-1 2 1 -4}, and target = 1.

    The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var threeSumClosest = function(nums, target) {
  var result = 0
  var INT_MAX = (2**31) - 1
  var distance = INT_MAX

  nums.sort(function(a, b) {
    return a - b
  })

  for (var i = 0; i < nums.length - 2; i++) {
    var j = i + 1
    var k = nums.length - 1
    while(j < k) {

      var sum = nums[i] + nums[j] + nums[k]
      var tempDistance = Math.abs(sum - target)
      
      if(tempDistance < distance) {
        distance = tempDistance
        result = sum
      }
      if(sum < target) j++
      else k--
    }
  }
  
  return result
};
```
