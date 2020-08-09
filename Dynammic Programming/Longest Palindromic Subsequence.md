<h1>Longest Palindromic Subsequence</h1>

<p>
Given a string A, find the common palindromic sequence ( A sequence which does not need to be contiguous and is a pallindrome), which is common in itself.

You need to return the length of longest palindromic subsequence in A.

NOTE:

    Your code will be run on multiple test cases (<=10). Try to come up with an optimised solution.

Problem Constraints

    1 <= |A|, |B| <= 1005
Input Format

    First argument is an string A.
Output Format
    
    Return a integer denoting the length of longest palindromic subsequence in A.
Example:

    Input 1:
        A = "bebeeed"
    Output 1:
        4
    Explanation 1:
        The longest common pallindromic subsequence is "eeee", which has a length of 4

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : string
    # @return an integer
    def solve(self, A):
        B = A[::-1]
        m,n = len(A),len(B)
        dp = [[0 for j in range(n+1)]for i in range(m+1)]
        
        for i in range(1,m+1):
            for j in range(1,n+1):
                if A[i-1] == B[j-1]:
                    dp[i][j] = 1+ dp[i-1][j-1]
                else:
                    dp[i][j] = max(dp[i][j-1],dp[i-1][j])
        
        return dp[m][n]
```