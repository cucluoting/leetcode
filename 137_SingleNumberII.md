# 137. Single Number II

Given an array of integers, every element appears three times except for one, which appears exactly once. Find that single one.

**Note:**
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
  var one = 0
  var two = 0
  var three = 0
  for (var i = 0; i < nums.length; i++) {
    two |= one & nums[i]
    one ^= nums[i]

    // 某一二进制为1的出现了一次+两次，将其放入three，并取反，使之将one和two与的时候将它们置为0
    three = ~(one & two)
    one &= three
    two &= three
  }
  return one
};
```
