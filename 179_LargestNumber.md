# 179. Largest Number

Given a list of non negative integers, arrange them such that they form the largest number.

For example, given `[3, 30, 34, 5, 9]`, the largest formed number is `9534330`.

Note: The result may be very large, so you need to return a string instead of an integer.

```javascript
/**
 * @param {number[]} nums
 * @return {string}
 */
var largestNumber = function(nums) {
  nums.sort(function(a, b) {
    var ab = a + '' + b
    var ba = b + '' + a
    return ba - ab
  });
  if (nums[0] === 0) return '0'
  return nums.join('')
};
```
