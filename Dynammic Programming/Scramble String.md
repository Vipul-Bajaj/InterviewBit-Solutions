<h1>Scramble String</h1>

<p>
Given a string A, we may represent it as a binary tree by partitioning it to two non-empty substrings recursively.

Below is one possible representation of A = “great”:

              great
             /    \
            gr    eat
           / \    /  \
          g   r  e   at
                     / \
                    a   t
 
To scramble the string, we may choose any non-leaf node and swap its two children.

For example, if we choose the node “gr” and swap its two children, it produces a scrambled string “rgeat”.

           rgeat
          /    \
         rg    eat
        / \    /  \
       r   g  e    at
                  / \
                 a   t
We say that “rgeat” is a scrambled string of “great”.

Similarly, if we continue to swap the children of nodes “eat” and “at”, it produces a scrambled string “rgtae”.

             rgtae
            /    \
           rg    tae
           / \   /  \
          r   g ta   e
                    / \
                   t   a
We say that “rgtae” is a scrambled string of “great”.

Given two strings A and B of the same length, determine if B is a scrambled string of S.

Input Format:

    The first argument of input contains a string A.
    The second argument of input contains a string B.
Output Format:

    Return an integer, 0 or 1:
        => 0 : False
        => 1 : True
Constraints:

    1 <= len(A), len(B) <= 50
Examples:

    Input 1:
        A = "we"
        B = "we"

    Output 1:
        1

    Input 2:
        A = "phqtrnilf"
        B = "ilthnqrpf"
        
    Output 2:
        0

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : string
    # @return an integer
    def isScramble(self, A, B):
        m,n = len(A),len(B)
    
        if m!=n:
            return 0
        
        if A == B:
            return 1
            
        dp = [[[0 for k in range(m)]for j in range(m)] for i in range(m)]
        
        for i in range(m):
            for j in range(m):
                dp[i][j][0] = 1 if A[i]==B[j] else 0
         
        
        for k in range(1,m):
            for i in range(m-k):
                for j in range(m-k):
                    dp[i][j][k] = 0
                    for p in range(k):
                        if ((dp[i][j][p] and dp[i+p+1][j+p+1][k-p-1])  or (dp[i][j+k-p][p] and dp[i+p+1][j][k-p-1])):
                            dp[i][j][k] = 1;  
                            break;  
                
        return dp[0][0][m-1]
```