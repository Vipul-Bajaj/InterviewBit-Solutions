<h1>Increasing Path in Matrix</h1>

<p>
Given a 2D integer matrix A of size N x M.

From A[i][j] you can move to A[i+1][j], if A[i+1][j] > A[i][j], or can move to A[i][j+1] if A[i][j+1] > A[i][j].

The task is to find and output the longest path length if we start from (0, 0).

NOTE:

    If there doesn't exist a path return -1.
Problem Constraints

    1 <= N, M <= 10^3
    1 <= A[i][j] <= 10^8
Input Format
    
    First and only argument is an 2D integer matrix A of size N x M.
Output Format
    
    Return a single integer denoting the length of longest path in the matrix if no such path exists return -1.
Example Input

    Input 1:
        A = [   [1, 2]
                [3, 4]
            ]
    Input 2:
        A = [   [1, 2, 3, 4]
                [2, 2, 3, 4]
                [3, 2, 3, 4]
                [4, 5, 6, 7]
            ]
    Output 1:
        3
    Output 2:
        7
    Explanation 1:
        Longest path is either 1 2 4 or 1 3 4.
    Explanation 2:
        Longest path is 1 2 3 4 5 6 7.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @return an integer
    def solve(self, A):
        m = len(A)
    
        if m<=0:
            return 0
        
        n = len(A[0])
        
        dp = [[0 for j in range(n)]for i in range(m)]
    
        dp[0][0] = 1
        
        for i in range(1,m):
            if A[i][0] > A[i-1][0] and dp[i-1][0]>0:
                dp[i][0] = max(dp[i][0],1 + dp[i-1][0])
                
        for j in range(1,n):
            if A[0][j] > A[0][j-1]  and dp[0][j-1]>0:
                dp[0][j] = max(dp[0][j],1 + dp[0][j-1])
        
        for i in range(1,m):
            for j in range(1,n):
                if A[i][j]>A[i-1][j] and dp[i-1][0]>0:
                    dp[i][j] = max(dp[i][j],1+dp[i-1][j])
                if A[i][j]>A[i][j-1] and dp[0][j-1]>0:
                    dp[i][j] = max(dp[i][j],1+dp[i][j-1])
                    
        return dp[m-1][n-1] if dp[m-1][n-1]>0 else -1
```