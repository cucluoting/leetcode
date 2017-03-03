# 69. Sqrt(x)

Implement `int sqrt(int x)`.

Compute and return the square root of x.

划重点**`int`**🙄️

```javascript
/**
 * @param {number} x
 * @return {number}
 */
var mySqrt = function(x) {
  if(x < 2) return x
  var left = 1,
      right = Math.floor(x / 2),
      result
  while(left <= right) {
    var mid = Math.floor(left + (right - left) / 2)
    if(x / mid > mid) {
      left = mid + 1
      result = mid
    }else if(x / mid < mid) {
      right = mid - 1
    }else {
      return mid
    }
  }
  return result
};
```
