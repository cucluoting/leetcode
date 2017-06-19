# 31. Next Permutation

Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending order).

The replacement must be in-place, do not allocate extra memory.

Here are some examples. Inputs are in the left-hand column and its corresponding outputs are in the right-hand column.

`1,2,3 → 1,3,2`  
`3,2,1 → 1,2,3`  
`1,1,5 → 1,5,1`  

- 知识点：全排列  

参考了Editorial Solution, 觉得按功能划分函数的思想特别好，便提取了`swap`和`rever`

```javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var nextPermutation = function(nums) {
  var i = nums.length - 2
  // 从右往左找出第一个不安升序排列的数字
  while (i >= 0 && nums[i] >= nums[i + 1]) {
    i--
  }
  if(i >= 0) {
    var j = nums.length - 1
    // 从右往左找出第一个比这个数字大的数字
    while(j >= i && nums[j] <= nums[i]) {
      j--
    }
    // 交换这两个数字
    swap(nums, i, j)
  }
  // 将该数字以后的数字倒序
  reverse(nums, i + 1)  
};

var swap = function(nums, i, j) {
  var temp = nums[i]
  nums[i] = nums[j]
  nums[j] = temp
};

var reverse = function(nums, start) {
  var i = start
  var j = nums.length - 1
  while (i < j) {
    swap(nums, i, j)
    i++
    j--
  }
};
```
