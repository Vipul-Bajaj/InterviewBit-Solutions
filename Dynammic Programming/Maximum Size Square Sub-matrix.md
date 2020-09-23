<h1>Maximum Size Square Sub-matrix</h1>

<p>
Given a 2D binary matrix A of size  N x M  find the area of maximum size square sub-matrix with all 1's.

Problem Constraints

    1 <= N, M <= 10^3
    A[i][j] = 1 or A[i][j] = 0
Input Format

    First argument is an 2D matrix A of size N x M.
Output Format
    
    Output the area of maximum size square sub-matrix in A with all 1's.
Example:

    Input 1:
        A = [
              [0, 1, 1, 0, 1],
              [1, 1, 0, 1, 0],
              [0, 1, 1, 1, 0],
              [1, 1, 1, 1, 0],
              [1, 1, 1, 1, 1],
              [0, 0, 0, 0, 0]
            ]
    Input 2:
        A = [
              [1, 1],
              [1, 1]
            ]
    Output 1:
        9
    Output 2:
        4
    Explanation 1:
        Consider the below binary matrix.
        <img src="https://imgur.com/50NQxJm">
        The area of the square is 3 * 3 = 9
    Explanation 2:
        The given matrix is the largest size square possible so area will be 2 * 2 = 4
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @return an integer
    def solve(self, A):
        m,n = len(A),len(A[0])
    
        s = [[0 for j in range(n)]for i in range(m)]
        
        for i in range(0, m): 
            for j in range(0, n):
                if i==0 or j==0:
                    s[i][j] = A[i][j]
                elif (A[i][j] == 1): 
                    s[i][j] = min(s[i][j-1], s[i-1][j],s[i-1][j-1]) + 1
                else: 
                    s[i][j] = 0
                    
        max_of_s = s[0][0] 
        max_i = 0
        max_j = 0
        for i in range(m): 
            for j in range(n): 
                if (max_of_s < s[i][j]): 
                    max_of_s = s[i][j] 
                    max_i = i 
                    max_j = j 
        
        # count = 0            
        # for i in range(max_i, max_i - max_of_s, -1): 
        #     for j in range(max_j, max_j - max_of_s, -1): 
        #         count+=1
                
        return max_of_s*max_of_s
```
