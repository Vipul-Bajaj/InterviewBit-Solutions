<h1>Coins in a Line</h1>

<p>
There are A coins (Assume A is even) in a line.Two players take turns to take a coin from one of the ends of the line until there are no more coins left.The player with the larger amount of money wins.

Assume that you go first.

Return the maximum amount of money you can win.

Input Format:

    The first and the only argument of input contains an integer array, A.
Output Format:

    Return an integer representing the maximum amount of money you can win.
Constraints:

    1 <= length(A) <= 500
    1 <= A[i] <= 1e5
Examples:

    Input 1:
        A = [1, 2, 3, 4]

    Output 1:
        6

    Explanation 1:
        
        You      : Pick 4
        Opponent : Pick 3
        You      : Pick 2
        Opponent : Pick 1
        
        Total money with you : 4 + 2 = 6

    Input 2:
        A = [5, 4, 8, 10]
        
    Output 2:
        15

    Explanation 2:

        You      : Pick 10
        Opponent : Pick 8
        You      : Pick 5
        Opponent : Pick 4
        
        Total money with you : 10 + 5 = 15

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def maxcoin(self, A):
        n = len(A)

        dp = [[[0,0] for j in range(n)] for i in range(n)]
        
        for i in range(n):
            dp[i][i][0] = A[i]
            
        
        for k in range(1,n):
            for i in range(n-1):
                j = i+k
                
                if j<n:
                    if(A[i]+dp[i+1][j][1]>=dp[i][j-1][1]+A[j]):
                        dp[i][j][0]=A[i]+dp[i+1][j][1]
                        dp[i][j][1]=dp[i+1][j][0]
                    else:
                        dp[i][j][0]=dp[i][j-1][1]+A[j]
                        dp[i][j][1]=dp[i][j-1][0]
        
        return dp[0][n-1][0]
```