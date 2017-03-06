# 70. Climbing Stairs

You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?


......斐波那契数列？一脸懵逼😁

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var climbStairs = function(n) {
  var f1 = 1,
      f2 = 2
  if(n === 1) {
    return f1
  }else if(n === 2) {
    return f2
  }
  for(var i = 3; i <= n; i++) {
    var f3 = f1 + f2
    f1 = f2
    f2 = f3
  }
  return f2
};
```
