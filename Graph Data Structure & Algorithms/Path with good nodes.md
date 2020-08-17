<h1>Path with good nodes</h1>

<p>
Given a tree with N nodes labelled from 1 to N.

Each node is either good or bad denoted by binary array A of size N where if A[i] is 1 then ithnode is good else if A[i] is 0 then ith node is bad.

Also the given tree is rooted at node 1 and you need to tell the number of root to leaf paths in the tree that contain not more than C good nodes.

NOTE:

    Each edge in the tree is bi-directional.

Problem Constraints

    2 <= N <= 10^5
    A[i] = 0 or A[i] = 1
    0 <= C <= N

Input Format:

    First argument is an binary integer array A of size N.
    Second argument is a 2-D array B of size (N-1) x 2 denoting the edge of the tree.
    Third argument is an integer C.

Output Format:

    Return an integer denoting the number of root to leaf paths in the tree that contain not more than C good nodes.

Example:

    Input 1:
        A = [0, 1, 0, 1, 1, 1]
        B = [  [1, 2]
                [1, 5]
                [1, 6]
                [2, 3]
                [2, 4]
            ]
        C = 1
    Output 1:
        3
    Explanation 1:
        Path (1 - 2 - 3) and (1 - 5) and (1 - 6) are the paths which contain atmost C nodes.

<h2>Solution</h2>

***

```python
def dfs(graph, vertex,c,A,B,C,ans):
    
    if A[vertex-1] == 1:
        c[0]+=1
        
    if len(graph[vertex]) == 0:
        if c[0] <= C:
            ans[0]+=1
    
    for node in graph[vertex] :
        dfs(graph, node,c,A,B,C,ans)
        
    if A[vertex-1] == 1:
        c[0]-=1

class Solution:
    # @param A : list of integers
    # @param B : list of list of integers
    # @param C : integer
    # @return an integer
    def solve(self, A, B, C):
        h = {}
        n = len(A)
        for i in range(1,n+1):
            h[i] = []
            
        for b in B:
            if b[0]<b[1]:
                h[b[0]].append(b[1])
            else:
                h[b[1]].append(b[0])
        
        ans = [0]
        
        dfs(h,1,[0],A,B,C,ans)
        
        return ans[0]
```