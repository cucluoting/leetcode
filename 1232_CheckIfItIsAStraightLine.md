# 1232. Check If It Is a Straight Line

You are given an array `coordinates`, `coordinates[i] = [x, y]`, where `[x, y]` represents the coordinate of a point. Check if these points make a straight line in the XY plane.

**Example 1:**

![](https://assets.leetcode.com/uploads/2019/10/15/untitled-diagram-2.jpg)

```
Input: coordinates = [[1,2],[2,3],[3,4],[4,5],[5,6],[6,7]]
Output: true
```

**Example 2:**

![](https://assets.leetcode.com/uploads/2019/10/09/untitled-diagram-1.jpg)

```
Input: coordinates = [[1,1],[2,2],[3,4],[4,5],[5,6],[7,7]]
Output: false
```

**Constraints:**

- 2 <= coordinates.length <= 1000
- coordinates[i].length == 2
- -10^4 <= coordinates[i][0], coordinates[i][1] <= 10^4
- coordinates contains no duplicate point.

```javascript
/**
 * @param {number[][]} coordinates
 * @return {boolean}
 */
var checkStraightLine = function (coordinates) {
  const [x1, y1] = coordinates[0];
  const [x2, y2] = coordinates[1];
  if (x2 !== x1) {
    const k = (y2 - y1) / (x2 - x1);
    const b = y1 - k * x1;
    for (let i = 2; i < coordinates.length; i++) {
      const [x, y] = coordinates[i];
      if (y !== k * x + b) {
        return false;
      }
    }
  } else {
    for (let i = 2; i < coordinates.length; i++) {
      const [x] = coordinates[i];
      if (x !== x1) {
        return false;
      }
    }
  }
  return true;
};

```
