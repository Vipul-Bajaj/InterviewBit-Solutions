<h1>Interleaving String</h1>

<p>
Given A, B, C, find whether C is formed by the interleaving of A and B.

Input Format:*

    The first argument of input contains a string, A.
    The second argument of input contains a string, B.
    The third argument of input contains a string, C.
Output Format:

    Return an integer, 0 or 1:
        => 0 : False
    => 1 : True
Constraints:

    1 <= length(A), length(B), length(C) <= 150
Examples:

    Input 1:
        A = "aabcc"
        B = "dbbca"
        C = "aadbbcbcac"

    Output 1:
        1
        
    Explanation 1:
        "aa" (from A) + "dbbc" (from B) + "bc" (from A) + "a" (from B) + "c" (from A)

    Input 2:
        A = "aabcc"
        B = "dbbca"
        C = "aadbbbaccc"

    Output 2:
        0

    Explanation 2:
        It is not possible to get C by interleaving A and B.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : string
    # @param C : string
    # @return an integer
    def isInterleave(self, A, B, C):
        i = 0
        j = 0
        k = 0
        m,n,l = len(A),len(B),len(C)
        
        dp = [[0 for j in range(n+1)] for i in range(m+1)]
        
        if m+n != l:
            return 0
            
        for i in range(m+1):
            for j in range(n+1):
                if i==0 and j==0:
                    dp[i][j] = 1
                
                elif i == 0:
                    if B[j-1]==C[j-1]:
                        dp[i][j] = dp[i][j-1]
                    
                elif j == 0:
                    if A[i-1]==C[i-1]:
                        dp[i][j] = dp[i-1][j]
                        
                elif A[i-1] == C[i+j-1] and B[j-1]!=C[i+j-1]:
                    dp[i][j] = dp[i-1][j]
                    
                elif B[j-1]==C[i+j-1] and A[i-1] != C[i+j-1]:
                    dp[i][j] = dp[i][j-1]
                
                elif B[j-1]==C[i+j-1] and A[i-1]==C[i+j-1]:
                    dp[i][j] = dp[i-1][j] or dp[i][j-1]
                    
        return dp[m][n]
```