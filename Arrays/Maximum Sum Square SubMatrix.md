<h1>Maximum Sum Square SubMatrix</h1>

<p>
Given a 2D integer matrix A of size N x N find a B x B submatrix where B<= N and B>= 1, such that sum of all the elements in submatrix is maximum.

Problem Constraints

    1 <= N <= 10^3.
    1 <= B <= N
    -10^2 <= A[i][j] <= 10^2.
Input Format

    First arguement is an 2D integer matrix A.
    Second argument is an integer B.
Output Format
    
    Return a single integer denoting the maximum sum of submatrix of size B x B.
Example:

    Input 1:
        A = [
                [1, 1, 1, 1, 1]
                [2, 2, 2, 2, 2]
                [3, 8, 6, 7, 3]
                [4, 4, 4, 4, 4]
                [5, 5, 5, 5, 5]
            ]
        B = 3
    Input 2:
        A = [
                [2, 2]
                [2, 2]
            ]
        B = 2
    Output 1:
        48
    Output 2:
        8
    Explanation 1:
        Maximum sum 3 x 3 matrix is
        8 6 7
        4 4 4
        5 5 5
        Sum = 48
    Explanation 2:
        Maximum sum 2 x 2 matrix is
        2 2
        2 2
        Sum = 8

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @param B : integer
    # @return an integer
    def solve(self, A, B):
        k = B
        (M, N) = (len(A), len(A[0]))
	
        mat_sum = [[0 for x in range(N)] for y in range(M)]
        mat_sum[0][0] = A[0][0]
        
        # pre-process first row
        for j in range(1, N):
        	mat_sum[0][j] = A[0][j] + mat_sum[0][j - 1]
        
        # pre-process first column
        for i in range(1, M):
        	mat_sum[i][0] = A[i][0] + mat_sum[i - 1][0]
        
        # pre-process rest of the matrix
        for i in range(1, M):
        	for j in range(1, N):
        		mat_sum[i][j] = A[i][j] + mat_sum[i - 1][j] + mat_sum[i][j - 1] - mat_sum[i - 1][j - 1]
        
        max_sum = float('-inf')
        
        for i in range(k - 1, M):
        	for j in range(k - 1, N):
        	    
        		total = mat_sum[i][j]
        		if i - k >= 0:
        			total = total - mat_sum[i - k][j]
        
        		if j - k >= 0:
        			total = total - mat_sum[i][j - k]
        
        		if i - k >= 0 and j - k >= 0:
        			total = total + mat_sum[i - k][j - k]
        
        		if total > max_sum:
        			max_sum = total
        
        return max_sum
```