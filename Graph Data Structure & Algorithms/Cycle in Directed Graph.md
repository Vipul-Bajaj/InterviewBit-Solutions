<h1>Cycle in Directed Graph</h1>

<p>
Given an directed graph having A nodes. A matrix B of size M x 2 is given which represents the M edges such that there is a edge directed from node B[i][0] to node B[i][1].

Find whether the graph contains a cycle or not, return 1 if cycle is present else return 0.

NOTE:

    1. The cycle must contain atleast two nodes.
    2. There are no self-loops in the graph.
    3. There are no multiple edges between two nodes.
    4. The graph may or may not be connected.
    5. Nodes are numbered from 1 to A.
    6. Your solution will run on multiple test cases. If you are using global variables make sure to clear them.

Problem Constraints

    2 <= A <= 105
    1 <= M <= min(200000,A(A-1))
    1 <= B[i][0], B[i][1] <= A

Input Format

    The first argument given is an integer A representing the number of nodes in the graph.
    The second argument given a matrix B of size M x 2 which represents the M edges such that there is a edge directed from node B[i][0] to node B[i][1].

Output Format

    Return 1 if cycle is present else return 0.

Example:

    Input 1:
        A = 5
        B = [  [1, 2] 
                [4, 1] 
                [2, 4] 
                [3, 4] 
                [5, 2] 
                [1, 3] ]
    Input 2:

        A = 5
        B = [  [1, 2]
                [2, 3] 
                [3, 4] 
                [4, 5] ]
    Output 1:
        1
    Output 2:
        0
    Explanation 1:
        The given graph contain cycle 1 -> 3 -> 4 -> 1 or the cycle 1 -> 2 -> 4 -> 1
    Explanation 2:
        The given graph doesn't contain any cycle.

<h2>Solution</h2>

***

```python
import sys
sys.setrecursionlimit(100000000)
def hasCycle(adj_dict,node,visited,recstack):
    visited[node] = True
    recstack[node] = True
    
    for neighbour in adj_dict[node]:
        if visited[neighbour] == False:
            if hasCycle(adj_dict,neighbour,visited,recstack):
                return True
        elif recstack[neighbour] == True:
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
                
        for node,neighbours in adj_dict.items():
            if visited[node] == False:
                if hasCycle(adj_dict,node,visited,recstack) == True:
                    return 1
        
        return 0
```