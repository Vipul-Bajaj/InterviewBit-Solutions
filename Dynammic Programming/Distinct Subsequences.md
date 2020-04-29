<h1>Distinct Subsequences</h1>

<p>
Given two sequences A, B, count number of unique ways in sequence A, to form a subsequence that is identical to the sequence B.

Subsequence : A subsequence of a string is a new string which is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (ie, “ACE” is a subsequence of “ABCDE” while “AEC” is not).

<b>Input Format:</b>

    The first argument of input contains a string, A.
    The second argument of input contains a string, B.
<b>Output Format:</b>

    Return an integer representing the answer as described in the problem statement.
<b>Constraints:</b>

    1 <= length(A), length(B) <= 700
<b>Example:</b>

    Input 1:
        A = "abc"
        B = "abc"
        
    Output 1:
        1

    Explanation 1:
        Both the strings are equal.

    Input 2:
        A = "rabbbit" 
        B = "rabbit"

    Output 2:
        3

    Explanation 2:
        These are the possible removals of characters:
            => A = "ra_bbit" 
            => A = "rab_bit" 
            => A = "rabb_it"
            
        Note: "_" marks the removed character.
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : string
    # @return an integer
    def numDistinct(self, A, B):
        if A == B:
            return 1
        
        m = len(A)
        n = len(B)
        if m<n:
            return 0
        
        dp = [[0 for j in range(m+1)] for i in range(n+1)]
        
        for i in range(0,n+1):
            for j in range(i,m+1):
                if i == 0:
                    dp[i][j] = 1
                elif j == 0:
                    continue
                elif A[j-1] == B[i-1]:
                    dp[i][j] = dp[i-1][j-1] +dp[i][j-1]
                else:
                    dp[i][j] = dp[i][j-1]
                    
        return dp[n][m]
```