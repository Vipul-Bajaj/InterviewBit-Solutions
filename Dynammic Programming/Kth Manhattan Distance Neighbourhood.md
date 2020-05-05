<h1>Kth Manhattan Distance Neighbourhood</h1>

<p>
Given a matrix M of size nxm and an integer K, find the maximum element in the K manhattan distance neighbourhood for all elements in nxm matrix.
In other words, for every element M[i][j] find the maximum element M[p][q] such that abs(i-p)+abs(j-q) <= K.

Note: Expected time complexity is O(N*N*K)

<b>Constraints:</b>

    1 <= n <= 300
    1 <= m <= 300
    1 <= K <= 300
    0 <= M[i][j] <= 1000
<b>Example:</b>

    Input:
        M  = [[1,2,4],[4,5,8]] , K = 2

    Output:
        ans = [[5,8,8],[8,8,8]]
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @param B : list of list of integers
    # @return a list of list of integers
    def solve(self, A, B):
        m = len(B)
        n = len(B[0])
        dp = [[[0 for k in range(n)]for j in range(m)]for i in range(A+1)]
        
        for k in range(0,A+1):
            for i in range(m):
                for j in range(n):
                    if k==0:
                        dp[0][i][j] = B[i][j]
                    else:
                        curr = -2**31
                        
                        if i>0:
                            curr = max(curr,dp[k-1][i-1][j])
                        if j>0:
                            curr = max(curr,dp[k-1][i][j-1])
                        if i<m-1:
                            curr = max(curr,dp[k-1][i+1][j])
                        if j<n-1:
                            curr = max(curr,dp[k-1][i][j+1])
    
                        dp[k][i][j] = max(curr,dp[k-1][i][j])
                        
        for i in range(m):
            for j in range(n):
                B[i][j] = dp[A][i][j]
                
        return B
```