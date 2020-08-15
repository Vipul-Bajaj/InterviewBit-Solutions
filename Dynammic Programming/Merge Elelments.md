<h1>Merge  Elements</h1>

<p>
Given an integer array A of size N. You have to merge all the elements of the array into one with the minimum possible cost.

The rule for merging is as follows:

1. Choose any two adjacent elements of the array with values say X and Y and merge them into a single element with value (X + Y) paying a total cost of (X + Y).

Return the minimum possible cost of merging all elements.

Problem Constraints:

    1 <= N <= 200
    1 <= A[i] <= 10^3
Input Format:

    First and only argument is an integer array A of size N.
Output Format:

    Return an integer denoting the minimum cost of merging all elements.
Example:

    Input 1:
        A = [1, 3, 7]
    Input 2:
        A = [1, 2, 3, 4]
    Output 1:
        15
    Output 2:
        19
    Explanation 1:
        All possible ways of merging:
        a) {1, 3, 7} (cost = 0) -> {4, 7} (cost = 4) -> {11} (cost = 4+11 = 15)
        b) {1, 3, 7} (cost = 0) -> {1, 10} (cost = 10) -> {11} (cost = 10+11 = 21)
        Thus, ans = 15

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def solve(self, A):
        n = len(A)
    
        dp = [[0 for j in range(n)]for i in range(n)]
        
        prefix = [0 for i in range(n)]
        
        prefix[0] = A[0]
        
        for i in  range(n):
            prefix[i] = prefix[i-1] + A[i]
            
        for i in range(0,n-1):
            dp[i][i+1] = A[i]+A[i+1]
        
        for diag in range(3,n+1):
            i = 0
            j = diag-1
            while j<n:
                dp[i][j] = 2**31
                for k in range(i,j):
                    c = dp[i][k]+dp[k+1][j]+(prefix[j]-(prefix[i-1] if i>0 else 0))
                    dp[i][j] = min (dp[i][j],c)
                i+=1
                j+=1
        
        return dp[0][n-1]
```