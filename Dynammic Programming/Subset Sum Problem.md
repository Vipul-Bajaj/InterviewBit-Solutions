<h1>Subset Sum Problem</h1>

<p>
Given an integer array A of size N.

You are also given an integer B, you need to find whether their exist a subset in A whose sum equal B.

If there exist a subset then return 1 else return 0.

Problem Constraints

    1 <= N <= 100
    1 <= A[i] <= 100
    1 <= B <= 105
Input Format

    First argument is an integer array A.
    Second argument is an integer B.
Output Format
    
    Return 1 if there exist a subset with sum B else return 0.
Example:

    Input 1:
        A = [3, 34, 4, 12, 5, 2]
        B = 9
    Input 2:
        A = [3, 34, 4, 12, 5, 2]
        B = 30
    Output 1:
        1
    Output 2:
        0
    Explanation 1:
        There is a subset (4, 5) with sum 9.
    Explanation 2:
        There is no subset that add up to 30.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return an integer
    def solve(self, A, B):
        n = len(A)
        dp = [[0 for j in range(B+1)]for i in range(n+1)]
        
        for i in range(n+1):
            dp[i][0] = 1
        
        for i in range(1, n + 1): 
            for j in range(1, B + 1): 
                if j<A[i-1]: 
                    dp[i][j] = dp[i-1][j] 
                if j>= A[i-1]: 
                    dp[i][j] = (dp[i-1][j] or dp[i - 1][j-A[i-1]]) 
        
        return  dp[n][B]
```