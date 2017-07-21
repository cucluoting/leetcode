# 56. Merge Intervals

Given a collection of intervals, merge all overlapping intervals.

For example,  
Given `[1,3],[2,6],[8,10],[15,18]`,  
return `[1,6],[8,10],[15,18]`.

```javascript
/**
 * Definition for an interval.
 * function Interval(start, end) {
 *     this.start = start;
 *     this.end = end;
 * }
 */
/**
 * @param {Interval[]} intervals
 * @return {Interval[]}
 */
var merge = function(intervals) {
  if (intervals.length === 0) return intervals
  intervals.sort(function(a, b) {
    if (a.start === b.start) return a.end - b.end
    return a.start - b.start
  });

  var result = [intervals[0]]
  for (var i = 0, len = intervals.length; i < len; i++) {
    var resultLastIndex = result.length - 1
    if (result[resultLastIndex].end >= intervals[i].start) {
      result[resultLastIndex].end = Math.max(result[resultLastIndex].end, intervals[i].end)
    } else {
      result.push(intervals[i])
    }
  }
  
  return result  
};
```
