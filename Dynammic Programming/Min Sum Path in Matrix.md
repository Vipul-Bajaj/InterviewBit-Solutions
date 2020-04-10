<h1>Min Sum Path in Matrix</h1>

<p>
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

    Note: You can only move either down or right at any point in time. 
Example :

    Input : 
        [  
            1 3 2
            4 3 1
            5 6 1
        ]

    Output : 8
        1 -> 3 -> 2 -> 1 -> 1

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @return an integer
    def minPathSum(self, A):
        m = len(A)
        
        if m<1:
            return 0
            
        n = len(A[0])
        
        dp = [[0 for j in range(n)]for i in range(m)]
        
        dp[0][0]=A[0][0]
        
        for i in range(m):
            for j in range(n):
                if i==0 and j==0:
                    continue
                elif i == 0:
                    dp[i][j] = dp[i][j-1] + A[i][j]
                elif j == 0:
                    dp[i][j] = dp[i-1][j] + A[i][j]
                else:
                    dp[i][j] = min(dp[i-1][j] + A[i][j],dp[i][j-1] + A[i][j])
                    
        return dp[m-1][n-1]
```