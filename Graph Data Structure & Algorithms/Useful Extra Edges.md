<h1>Useful Extra Edges</h1>

<p>
Given a graph of A nodes. Also given the weighted edges in the form of array B.
You are also given starting point C and destination point D.
Also given are some extra edges in the form of vector E.
You need to find the length of the shortest path from C to D if you can use maximum one road from the given roads in E.
All roads are one way ie they go from B[i][0] to B[i][1].

Problem Constraints

    1 <= A <= 100000
    1 <= |B| <= 100000
    1 <= C, D <= A
    1 <= |E| <= 300
    All lengths of the roads lie between 1 and 1000.

Input Format

    First argument is the integer A.
    Second argument is the vector of vectors B.
    Third argument is the integer C.
    Fourth argument is the integer D.
    Fifth argument is the vector of vectors E.

Output Format

    Return -1 if C is not reachable from D. Else return the shortest distance between them.

Example:

    Input 1:
        A = 3
        B = [   [1, 2, 1]
              [2, 3, 2]
          ]
        C = 1
        D = 3
        E = [   [1, 3, 2]
          ]
    Input 2:
        A = 4
        B = [   [1, 2, 1]
                [2, 3, 2]
                [3, 1, 4]
            ]
        C = 1
        D = 4
        E = [   [1, 3, 2]
            ]
    Output 1:
        2
    Output 2:
        -1
    Explanation 1:
        Use the direct edge from 1 to 3. It has shortest path from 1 to 3.
    Explanation 2:
        4 cannot be reached from 1.

<h2>Solution</h2>

***

```python
from copy import deepcopy
from collections import deque
class Solution:
    # @param A : integer
    # @param B : list of list of integers
    # @param C : integer
    # @param D : integer
    # @param E : list of list of integers
    # @return an integer
    def solve(self, A, B, C, D, E):
        if C == D:
            return 0
            
        graph = {}
        
        for i in range(A+1):
            graph[i] = []
            
        n = len(B)
        for i in range(n):
            graph[B[i][0]].append((B[i][1],B[i][2]))
            
        n = len(E)
        
        shortest = 2**31
        for k in range(n):
            if E[k][0]>A or E[k][1]>A:
                continue
            
            new_graph = deepcopy(graph)
            
            dist = [2**31] * (A+1)
            dist[C] = 0
            new_graph[E[k][0]].append((E[k][1],E[k][2]))
            new_graph[E[k][1]].append((E[k][0],E[k][2]))
            
            q = deque([(0,C)])
            
            while q:
                node = q.popleft()
                
                w,s = node
                
                for i in range(len(new_graph[s])):
                    if dist[new_graph[s][i][0]]>w+new_graph[s][i][1]:
                        dist[new_graph[s][i][0]]=w+new_graph[s][i][1]
                        q.append((dist[new_graph[s][i][0]],new_graph[s][i][0]))
            
            
            shortest = min(shortest,dist[D])
            
            if shortest == 2**31:
                return -1
                
        return shortest if shortest != 2**31 else -1
```
