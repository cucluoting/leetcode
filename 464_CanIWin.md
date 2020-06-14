# 464. Can I Win

In the "100 game," two players take turns adding, to a running total, any integer from 1..10. The player who first causes the running total to reach or exceed 100 wins.

What if we change the game so that players cannot re-use integers?

For example, two players might take turns drawing from a common pool of numbers of 1..15 without replacement until they reach a total >= 100.

Given an integer `maxChoosableInteger` and another integer `desiredTotal`, determine if the first player to move can force a win, assuming both players play optimally.

You can always assume that `maxChoosableInteger` will not be larger than 20 and `desiredTotal` will not be larger than 300.

```javascript
/**
 * @param {number} maxChoosableInteger
 * @param {number} desiredTotal
 * @return {boolean}
 */
var canIWin = function(maxChoosableInteger, desiredTotal) {
  if (maxChoosableInteger >= desiredTotal) {
    return true
  }
  if (maxChoosableInteger * (maxChoosableInteger + 1) / 2 < desiredTotal) {
    return false
  }
  const map = new Map()
  return canWin(maxChoosableInteger, desiredTotal, 0, map)
};

var canWin = function(length, total, used, map) {
  if (map.get(used)) {
    return map.get(used)
  }
  for (let i = 0; i < length; i++) {
    const curr = (1 << i)
    if ((curr & used) === 0) {
      if (total <= i + 1 || !canWin(length, total - (i + 1), curr | used, map)) {
        map.set(used, true)
        return true
      }
    }
  }
  map.set(used, false)
  return false
}
```
