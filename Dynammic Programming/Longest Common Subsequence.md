<h1>Longest Common Subsequence</h1>

<p>
Given two strings A and B. Find the longest common sequence ( A sequence which does not need to be contiguous), which is common in both the strings.

You need to return the length of such longest common subsequence.

Problem Constraints

    1 <= |A|, |B| <= 1005
Input Format

    First argument is an string A.
    Second argument is an string B.
Output Format
    
    Return the length of such longest common subsequence between string A and string B.
Example:

    Input 1:
        A = "abbcdgf"
        B = "bbadcgf"
    Output 1:
        5
    Explanation 1:
        The longest common subsequence is "bbcgf", which has a length of 5

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : string
    # @return an integer
    def solve(self, A, B):
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