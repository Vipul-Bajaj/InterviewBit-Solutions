<h1>Max Sum Without Adjacent Elements</h1>

<p>
Given a 2 x N grid of integer, A, choose numbers such that the sum of the numbers
is maximum and no two chosen numbers are adjacent horizontally, vertically or diagonally, and return it.

Note: You can choose more than 2 numbers.

<b>Input Format:</b>

    The first and the only argument of input contains a 2d matrix, A.
<b>Output Format:</b>

    eturn an integer, representing the maximum possible sum.
<b>Constraints:</b>

    1 <= N <= 20000
    1 <= A[i] <= 2000

<b>Examples:</b>

    Input 1:
        A = [   [1]
                [2]    ]

    Output 1:
        2

    Explanation 1:
        We will choose 2.

    Input 2:
        A = [   [1, 2, 3, 4]
                [2, 3, 4, 5]    ]
        
    Output 2:
        8
    
    Explanation 2:
        We will choose 3 and 5.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @return an integer
    def adjacent(self, A):
        m = len(A)
    
        n = len(A[0])
        
        if n == 1:
            return max(max(x) for x in A)
            
        dp = [[0 for j in range(n)]for i in range(m)]
        
        for i in range(m):
            for j in range(2):
                dp[i][j] = A[i][j]
        
        for j in range(2,n):
            if j-2>=0:
                dp[0][j] = max(A[0][j],A[0][j]+dp[0][j-2],A[0][j]+dp[1][j-2])
                dp[1][j] = max(A[1][j],A[1][j]+dp[0][j-2],A[1][j]+dp[1][j-2])
            if j-3>=0:
                dp[0][j] = max(dp[0][j],A[0][j],A[0][j]+dp[0][j-3],A[0][j]+dp[1][j-3])
                dp[1][j] = max(dp[1][j],A[1][j],A[1][j]+dp[0][j-3],A[1][j]+dp[1][j-3])
        
        # print(dp)
        return max(max(x) for x in dp)
```