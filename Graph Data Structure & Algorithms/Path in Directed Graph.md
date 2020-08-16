<h1>Path in Directed Graph</h1>

<p>
Given an directed graph having A nodes labelled from 1 to A containing M edges given by matrix B of size M x 2such that there is a edge directed from node

B[i][0] to node B[i][1].

Find whether a path exists from node 1 to node A.

Return 1 if path exists else return 0.

NOTE:

1. There are no self-loops in the graph.
2. There are no multiple edges between two nodes.
3. The graph may or may not be connected.
4. Nodes are numbered from 1 to A.
5. Your solution will run on multiple test cases. If you are using global variables make sure to clear them.

Problem Constraints

    2 <= A <= 105
    1 <= M <= min(200000,A(A-1))
    1 <= B[i][0], B[i][1] <= A

Input Format:

    The first argument given is an integer A representing the number of nodes in the graph.
    The second argument given a matrix B of size M x 2 which represents the M edges such that there is a edge directed from node B[i][0] to node B[i][1].
Output Format:

    Return 1 if path exists between node 1 to node A else return 0.

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
        0
    Output 2:
        1
    Explanation 1:
        The given doens't contain any path from node 1 to node 5 so we will return 0.
    Explanation 2:
        Path from node1 to node 5 is ( 1 -> 2 -> 3 -> 4 -> 5 ) so we will return 1.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @param B : list of list of integers
    # @return an integer
    def solve(self, A, B):
        h = {}
        for i in range(1,A+1):
            h[i] = []
            
        for b in B:
            if b[0] in h:
                h[b[0]].append(b[1])
            else:
                h[b[0]] = [b[1]]
                
        q= [1]
        
        visited = [False for i in range(A+1)]
        while q:
            node = q.pop(0)
            visited[node] = True
            if node == A:
                return 1
            
            for n in h[node]:
                if visited[n] == False:
                    q.append(n)
        
        return 0
```