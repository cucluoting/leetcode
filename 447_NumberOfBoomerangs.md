# 447. Number of Boomerangs

Given n points in the plane that are all pairwise distinct, a "boomerang" is a tuple of points (i, j, k) such that the distance between i and j equals the distance between i and k (**the order of the tuple matters**).

Find the number of boomerangs. You may assume that n will be at most 500 and coordinates of points are all in the range **[-10000, 10000]** (inclusive).

**Example:**
```
Input:
[[0,0],[1,0],[2,0]]

Output:
2

Explanation:
The two boomerangs are [[1,0],[0,0],[2,0]] and [[1,0],[2,0],[0,0]]
```

```javascript
/**
 * @param {number[][]} points
 * @return {number}
 */
var numberOfBoomerangs = function(points) {
  let result = 0
  for (let i = 0; i < points.length; i++) {
    const distances = new Map()
    for (let j = 0; j < points.length; j++) {
      if (i === j) {
        continue
      }
      const dx = points[j][0] - points[i][0];
      const dy = points[j][1] - points[i][1];
      const distance = dx * dx + dy * dy
      distances.set(distance, distances.has(distance) ? distances.get(distance) + 1 : 1)
    }
    for (const val of distances.values()) {
      result += val * (val - 1)
    }
  }
  return result
};
```
