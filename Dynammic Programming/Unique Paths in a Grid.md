<h1>Unique Paths in a Grid</h1>

<p>
Given a grid of size m * n, lets assume you are starting at (1,1) and your goal is to reach (m,n). At any instance, if you are on (x,y), you can either go to (x, y + 1) or (x + 1, y).

Now consider if some obstacles are added to the grids. How many unique paths would there be?
An obstacle and empty space is marked as 1 and 0 respectively in the grid.

Example :
There is one obstacle in the middle of a 3x3 grid as illustrated below.

    [
        [0,0,0],
        [0,1,0],
        [0,0,0]
    ]

The total number of unique paths is 2.

    Note: m and n will be at most 100. 

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @return an integer
    def uniquePathsWithObstacles(self, A):
        m = len(A)
        if m < 1:
            return 0
        n = len(A[0])
        
        if m==1 and n==1:
            return 0 if A[0][0] else 1
            
        dp = [[0 for j in range(n)]for i in range(m)]
        
        dp[0][0] = 1 if A[0][0] == 0 else 0
        
        for i in range(m):
            for j in range(n):
                if i == 0 and j == 0:
                    continue
                elif i == 0:
                    dp[i][j] = 1 if A[i][j] == 0 and dp[i][j-1]!=0 else 0
                elif j == 0:
                    dp[i][j] = 1 if A[i][j] == 0 and dp[i-1][j]!=0 else 0
                else:
                    dp[i][j] = dp[i-1][j]+dp[i][j-1] if A[i][j]==0 else 0
                    
        return dp[m-1][n-1]
```