<h1>Cycle in Undirected Graph</h1>

<p>
Given an undirected graph having A nodes labelled from 1 to A with M edges given in a form of matrix B of size M x 2 where (B[i][0], B[i][1]) represents two nodes B[i][0] and B[i][1] connected by an edge.

Find whether the graph contains a cycle or not, return 1 if cycle is present else return 0.

NOTE:

    1. The cycle must contain atleast three nodes.
    2. There are no self-loops in the graph.
    3. There are no multiple edges between two nodes.
    4. The graph may or may not be connected.
    5. Nodes are numbered from 1 to A.
    6. Your solution will run on multiple test cases. If you are using global variables make sure to clear them.

Problem Constraints

    1 <= A, M <= 3105
    1 <= B[i][0], B[i][1] <= A

Input Format

    The first argument given is an integer A representing the number of nodes in the graph.
    The second argument given is an matrix B of size M x 2 which represents the M edges such that there is a edge between node B[i][0] and node B[i][1].

Output Format

    Return 1 if cycle is present else return 0.

Example:

    Input 1:
        A = 5
        B = [  [1. 2]
                [1, 3]
                [2, 3]
                [1, 4]
                [4, 5]
            ]
    Input 2:
        A = 3
        B = [  [1. 2]
                [1, 3]
        ]
    Output 1:
        1
    Output 2:
        0
    Explanation 1:
        There is a cycle in the graph i.e 1 -> 2 -> 3 -> 1 so we will return 1
    Explanation 2:
        No cycle present in the graph so we will return 0.

<h2>Solution</h2>

***

```python
def hasCycle(adj_dict,node,visited,recstack,parent):
    visited[node] = True
    recstack[node] = True
    
    for neighbour in adj_dict[node]:
        if visited[neighbour] == False and neighbour != parent:
            if hasCycle(adj_dict,neighbour,visited,recstack,node):
                return True
        elif recstack[neighbour] == True and neighbour != parent:
            return True
    recstack[node] = False
    return False
class Solution:
    # @param A : integer
    # @param B : list of list of integers
    # @return an integer
    def solve(self, A, B):
        visited = [False]*(A+1)
        recstack = [False]*(A+1)
        
        adj_dict = {}
        for i in range(1,A+1):
            adj_dict[i] = []
        for i in range(len(B)):
            adj_dict[B[i][0]].append(B[i][1])
            adj_dict[B[i][1]].append(B[i][0])
                
        for node,neighbours in adj_dict.items():
            if visited[node] == False:
                if hasCycle(adj_dict,node,visited,recstack,node) == True:
                    return 1
        
        return 0
```