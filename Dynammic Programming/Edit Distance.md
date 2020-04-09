<h1>Edit Distance</h1>

<p>
Given two strings A and B, find the minimum number of steps required to convert A to B. (each operation is counted as 1 step.)

You have the following 3 operations permitted on a word:

Insert a character
Delete a character
Replace a character


Input Format:

    The first argument of input contains a string, A.
    The second argument of input contains a string, B.
Output Format:

    Return an integer, representing the minimum number of steps required.
Constraints:

    1 <= length(A), length(B) <= 450
Examples:

    Input 1:
        A = "abad"
        B = "abac"

    Output 1:
        1

    Explanation 1:
        Operation 1: Replace d with c.

    Input 2:
        A = "Anshuman"
        B = "Antihuman"

    Output 2:
        2

    Explanation 2:
        => Operation 1: Replace s with t.
        => Operation 2: Insert i.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : string
    # @return an integer
    def minDistance(self, A, B):
        m,n = len(A),len(B)
        dp = [[0 for j in range(n+1)]for i in range(m+1)]
        
        for i in range(m+1):
            for j in range(n+1):
                if i == 0:
                    dp[i][j] = j
                    
                elif j == 0:
                    dp[i][j] = i
                    
                elif A[i-1] == B[j-1]:
                    dp[i][j] = dp[i-1][j-1]
                    
                else:
                    dp[i][j] = 1 + min(dp[i-1][j],dp[i-1][j-1],dp[i][j-1])
        
        return dp[m][n]
```