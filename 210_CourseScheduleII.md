# 210. Course Schedule II

There are a total of n courses you have to take, labeled from `0` to `n - 1`.

Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair: `[0,1]`

Given the total number of courses and a list of prerequisite **pairs**, return the ordering of courses you should take to finish all courses.

There may be multiple correct orders, you just need to return one of them. If it is impossible to finish all courses, return an empty array.

For example:  
```
2, [[1,0]]
```

There are a total of 2 courses to take. To take course 1 you should have finished course 0. So the correct course order is `[0,1]`

```
4, [[1,0],[2,0],[3,1],[3,2]]
```

There are a total of 4 courses to take. To take course 3 you should have finished both courses 1 and 2. Both courses 1 and 2 should be taken after you finished course 0. So one correct course order is `[0,1,2,3]`. Another correct ordering is`[0,2,1,3]`.

**Note:**  
1. The input prerequisites is a graph represented by **a list of edges**, not adjacency matrices. Read more about [how a graph is represented](https://www.khanacademy.org/computing/computer-science/algorithms/graph-representation/a/representing-graphs).
2. You may assume that there are no duplicate edges in the input prerequisites.

**Hints:**  
1. This problem is equivalent to finding the topological order in a directed graph. If a cycle exists, no topological ordering exists and therefore it will be impossible to take all courses.
2. [Topological Sort via DFS](https://www.coursera.org/specializations/algorithms) - A great video tutorial (21 minutes) on Coursera explaining the basic concepts of Topological Sort.
3. Topological sort could also be done via [BFS](https://en.wikipedia.org/wiki/Topological_sorting#Algorithms).

- 相关题目[207. Course Schedule](https://github.com/cucluoting/leetcode/blob/master/207_CourseSchedule.md)

```javascript
/**
 * @param {number} numCourses
 * @param {number[][]} prerequisites
 * @return {number[]}
 */
var findOrder = function(numCourses, prerequisites) {
  var edges = []
  var countOfIndegree = []

  for (var i = 0; i < numCourses; i++) {
    edges[i] = []
    countOfIndegree[i] = 0
  }

  for (var i = 0; i < prerequisites.length; i++) {
    var inPoint = prerequisites[i][0]
    var outPoint = prerequisites[i][1]
    edges[inPoint].push(outPoint)
    ++countOfIndegree[outPoint]
  }

  var queue = []
  var result = []
  countOfIndegree.forEach(function(count, index) {
    if (count === 0) {
      queue.push(index)
    }
  })

  while(queue.length) {
    var indegree = queue.shift()
    result.unshift(indegree)
    edges[indegree].forEach(function(outPoint) {
      if (--countOfIndegree[outPoint] === 0) {
        queue.push(outPoint)
      }
    })
  }
  return result.length === numCourses ? result : []
};
```
