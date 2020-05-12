<h1>Clone Graph</h1>

<p>
Clone an undirected graph. Each node in the graph contains a label and a list of its neighbors.

<h2>Solution</h2>

***

```python
# Definition for a undirected graph node
# class UndirectedGraphNode:
#     def __init__(self, x):
#         self.label = x
#         self.neighbors = []

class Solution:
    # @param node, a undirected graph node
    # @return a undirected graph node
    def cloneGraph(self, node):
        visited={}
        def clone(node,visited):
            if node not in visited:
                new_node = UndirectedGraphNode(node.label)
                visited[node] = new_node
                new_node.neighbors = [clone(n,visited) for n in node.neighbors]
            return visited[node]
        clone(node,visited)
        return visited[node]
```