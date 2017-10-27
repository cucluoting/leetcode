# 133. Clone Graph

Clone an undirected graph. Each node in the graph contains a `label` and a list of its `neighbors`.


**OJ's undirected graph serialization:**  
Nodes are labeled uniquely.

We use `#` as a separator for each node, and `,` as a separator for node label and each neighbor of the node.  
As an example, consider the serialized graph `{0,1,2#1,2#2,2}`.  

The graph has a total of three nodes, and therefore contains three parts as separated by `#`.

1. First node is labeled as `0`. Connect node `0` to both nodes `1` and `2`.
2. Second node is labeled as `1`. Connect node `1` to node `2`.
3. Third node is labeled as `2`. Connect node `2` to node `2` (itself), thus forming a self-cycle.

Visually, the graph looks like the following:

```
       1
      / \
     /   \
    0 --- 2
         / \
         \_/
```

```javascript
/**
 * Definition for undirected graph.
 * function UndirectedGraphNode(label) {
 *     this.label = label;
 *     this.neighbors = [];   // Array of UndirectedGraphNode
 * }
 */

/**
 * @param {UndirectedGraphNode} graph
 * @return {UndirectedGraphNode}
 */
var cloneGraph = function(graph) {
  return dfs(graph, {})
};

var dfs = function(node, visited) {
  if (!node) return node
  if (visited[node.label]) return visited[node.label]
  var newNode = new UndirectedGraphNode(node.label)
  visited[node.label] = newNode

  for (var i = 0, len = node.neighbors.length; i < len; i++) {
    var neighbor = node.neighbors[i]    
    newNode.neighbors.push(dfs(neighbor, visited))
  }
  return newNode
};
```
