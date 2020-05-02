<h1>Regular Expression Match II</h1>

<p>
Implement regular expression matching with support for '.' and '*'.

    '.' Matches any single character.
    '*' Matches zero or more of the preceding element.

The matching should cover the entire input string (not partial).

The function prototype should be:

    int isMatch(const char *s, const char *p)
Some examples:

    isMatch("aa","a") → 0
    isMatch("aa","aa") → 1
    isMatch("aaa","aa") → 0
    isMatch("aa", "a*") → 1
    isMatch("aa", ".*") → 1
    isMatch("ab", ".*") → 1
    isMatch("aab", "c*a*b") → 1

Return 0 / 1 ( 0 for false, 1 for true ) for this problem

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : string
    # @return an integer
    def isMatch(self, A, B):
        m = len(A)
        n = len(B)
        dp = [[0 for j in range(n+1)]for i in range(m+1)]
        
        dp[0][0] = 1
        
        for i in range(2,n+1):
            dp[0][i]  = dp[0][i-2] if B[i-1]=='*' else 0
    
        for i in range(1,m+1):
            for j in range(1,n+1):
                if B[j-1] == '.' or A[i-1]==B[j-1]:
                    dp[i][j] = dp[i-1][j-1]
                elif B[j-1]=="*":
                    dp[i][j] = dp[i][j-2]
                    if B[j-2] == '.' or A[i-1]==B[j-2]:
                        dp[i][j] = dp[i][j] or dp[i-1][j]
                        
                    
        return dp[m][n]
```