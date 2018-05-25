# 223. Rectangle Area

Find the total area covered by two **rectilinear** rectangles in a **2D** plane.

Each rectangle is defined by its bottom left corner and top right corner as shown in the figure.

![](https://leetcode.com/static/images/problemset/rectangle_area.png)

**Example:**

```
Input: -3, 0, 3, 4, 0, -1, 9, 2
Output: 45
```

**Note:**
Assume that the total area is never beyond the maximum possible value of **int**.

```javascript
/**
 * @param {number} A
 * @param {number} B
 * @param {number} C
 * @param {number} D
 * @param {number} E
 * @param {number} F
 * @param {number} G
 * @param {number} H
 * @return {number}
 */
var computeArea = function(A, B, C, D, E, F, G, H) {
  const area = (C - A) * (D - B) + (G - E) * (H - F)
  return area - Math.max(Math.min(C, G) - Math.max(A, E), 0) * Math.max(Math.min(D, H) - Math.max(B, F), 0)
};
```
