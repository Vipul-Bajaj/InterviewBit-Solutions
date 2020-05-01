<h1>Regular Expression Match</h1>

<p>
Implement wildcard pattern matching with support for ‘?’ and ‘*’ for strings A and B.

1. ’?’ : Matches any single character.
2. ‘*’ : Matches any sequence of characters (including the empty sequence).
The matching should cover the entire input string (not partial).

Input Format:

    The first argument of input contains a string A.
    The second argument of input contains a string B.
Output Format:

    Return 0 or 1:
        => 0 : If the patterns do not match.
        => 1 : If the patterns match.
Constraints:

    1 <= length(A), length(B) <= 9e4
Examples:

    Input 1:
        A = "aa"
        B = "a"

    Output 1:
        0

    Input 2:
        A = "aa"
        B = "aa"

    Output 2:
        1

    Input 3:
        A = "aaa"
        B = "aa"

    Output 3:
        0
        
    Input 4:
        A = "aa"
        B = "*"

    Output 4:
        1

    Input 5:
        A = "aa"
        B = "a*"

    Output 5:
        1

    Input 6:
        A = "ab"
        B = "?*"

    Output 6:
        1

    Input 7:
        A = "aab"
        B = "c*a*b"

    Output 7:
        0

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : string
    # @return an integer
    def isMatch(self, A, B): 
        # DP Approach time complexity O(m*n)
        # m = len(A)
        # n = len(B)
        # dp = [[0 for j in range(n+1)]for i in range(m+1)]
        
        # dp[0][0] = 1
        
        # for i in range(1,n+1):
        #     dp[0][i]  = dp[0][i-1] if B[i-1]=="*" else 0
    
        # for i in range(1,m+1):
        #     for j in range(1,n+1):
        #         if B[j-1] == '?' or A[i-1]==B[j-1]:
        #             dp[i][j] = dp[i-1][j-1]
        #         elif B[j-1]=="*":
        #             dp[i][j] = dp[i-1][j] or dp[i][j-1]
                    
        # return dp[m][n]
        # Non-DP Approach time complexity O(n)
        m = len(A)
        n = len(B)
        if (m == 0): 
            return 1 if (n == 0) else 0
    
        i = 0
        j = 0
        index_A = -1
        index_B = -1
        while(i < m): 
            if (j < n and A[i] == B[j]): 
                i += 1
                j += 1
    
            elif(j < n and B[j] == '?'): 
                i += 1
                j += 1
    
            elif(j < n and B[j] == '*'): 
                index_A = i 
                index_B = j 
                j += 1
    
            elif(index_B != -1): 
                j = index_B + 1
                i = index_A + 1
                index_A += 1
    
            else: 
                return 0
    
        while (j < n and B[j] == '*'): 
            j += 1
    
        if(j == n): 
            return 1
      
        return 0
```