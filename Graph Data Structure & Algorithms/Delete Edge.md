<h1>Delete Edge</h1>

<p>
Given a undirected tree with N nodes labeled from 1 to N.

Each node has a certain weight assigned to it given by an integer array A of size N.

You need to delete an edge in such a way that Product between sum of weight of nodes in one subtree with sum of weight of nodes in other subtree is maximized.

Return this maximum possible product modulo 10^9 + 7.

NOTE:

    The tree is rooted at node labeled with 1.

Problem Constraints

    2 <= N <= 10^5
    1 <= A[i] <= 10^3

Input Format:

    First argument is an integer array A of size N denoting the weight of each node.
    Second argument is a 2-D array B of size (N-1) x 2 denoting the edge of the tree.

Output Format:

    Return a single integer denoting the maximum product prossible of sum of weights of nodes in the two subtrees formed by deleting an edge with modulo 109 + 7.

Example:

    Input 1:
        A = [10, 5, 12, 6]
        B = [
                [1, 2]
                [1, 4]
                [4, 3]
            ]
    Input 2:
        A = [11, 12]
        B = [
                [1, 2]
            ]
    Output 1:
        270
    Output 2:
        132
    Explanation 1:
        Removing edge (1, 4) created two subtrees.
        Subtree-1 contains nodes (1, 2) and Subtree-2 contains nodes (3, 4)
        So product will be = (A[1] + A[2]) * (A[3] + A[4]) = 15 * 18 = 270
    Explanation 2:
        Removing edge (1, 2) created two subtrees.
        Subtree-1 contains node (1) and Subtree-2 contains node (3)
        So product will be = (A[1]) * (A[2]) = 11 * 12 = 132

<h2>Solution</h2>

***

```python
def dfs(u,parent,total_sum,graph,subtree,ans):
    s = subtree[u-1]  
    for i in range(len(graph[u])): 
        v = graph[u][i]  
        if (v != parent): 
            dfs(v, u, total_sum, graph,  
                        subtree, ans)  
            s += subtree[v-1] 

    subtree[u-1] = s
    
    if u !=1:
        ans[0] = max(ans[0],(s*(total_sum-s))%((10**9)+7))

class Solution:
    # @param A : list of integers
    # @param B : list of list of integers
    # @return an integer
    def deleteEdge(self, A, B):
        n = len(A)
        total_sum = sum(A)
        
        graph = {}
        for i in  range(n):
            graph[i+1] = []
            
        for i,j in B:
            graph[i].append(j)
            graph[j].append(i)
        
        ans =[0]
        
        dfs(1,0,total_sum,graph,A,ans)
        
        return ans[0]%((10**9)+7)
```