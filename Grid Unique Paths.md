<h1>Grid Unique Paths</h1>

<p>

A robot is located at the top-left corner of an A x B grid (marked ‘Start’ in the diagram below).

<img src="https://i.imgur.com/3eaivQ5.png">

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked ‘Finish’ in the diagram below).

How many possible unique paths are there?

    Note: A and B will be such that the resulting answer fits in a 32 bit signed integer.

Example :

    Input : A = 2, B = 2
    Output : 2

    2 possible routes : (0, 0) -> (0, 1) -> (1, 1) 
                OR  : (0, 0) -> (1, 0) -> (1, 1)
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @param B : integer
    # @return an integer
    def uniquePaths(self, A, B):
        dp = [[0 for j in range(B)]for i in range(A)]
        
        for i in range(0,B):
            dp[0][i] = 1
        
        for i in range(0,A):
            dp[i][0] = 1
            
        for i in range(1,A):
            for j in range(1,B):
                dp[i][j] = dp[i-1][j]+dp[i][j-1]
                
        return dp[A-1][B-1]
```