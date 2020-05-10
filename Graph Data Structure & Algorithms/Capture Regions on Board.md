<h1>Capture Regions on Board</h1>

<p>
Given a 2D board containing 'X' and 'O', capture all regions surrounded by 'X'.

A region is captured by flipping all 'O's into 'X's in that surrounded region.

Input Format:

    First and only argument is a N x M character matrix A
Output Format:

    make changes to the the input only as matrix is passed by reference.
Constraints:

    1 <= N,M <= 1000
For Example:

    Input 1:
        A = [ [X, X, X, X],
            [X, O, O, X],
            [X, X, O, X],
            [X, O, X, X] ]
    Output 1:
        After running your function, the board should be:
        A = [ [X, X, X, X],
            [X, X, X, X],
            [X, X, X, X],
            [X, O, X, X] ]
    Explanation:
        O in (4,2) is not surrounded by X from below.

<h2>Solution</h2>

***

```python
def floodFill(mat, rows,col,i,j,previous_value, new_value):
        
    if i < 0 or j < 0 or i >= rows or j >= col: 
        return
    
    if mat[i][j] != previous_value:
        return
    
    mat[i][j] = new_value
        
    floodFill(mat, rows,col,i-1,j,previous_value, new_value)
    floodFill(mat, rows,col,i+1,j,previous_value, new_value)
    floodFill(mat, rows,col,i,j-1,previous_value, new_value)
    floodFill(mat, rows,col,i,j+1,previous_value, new_value)
    
class Solution:
    # @param A : list of list of chars
    def solve(self, A):
        m = len(A)
        n = len(A[0])
        for i in range(m):
            for j in range(n):
                if "O" == A[i][j]:
                    A[i][j] = '-'
                    
        for i in range(m):
            if A[i][0] == '-':
                floodFill(A,m,n,i,0,'-','O')
                
        for i in range(m):
            if A[i][n-1] == '-':
                floodFill(A,m,n,i,n-1,'-','O')
                
        for j in range(n):
            if A[0][j] == '-':
                floodFill(A,m,n,0,j,'-','O')
                
        for j in range(n):
            if A[m-1][j] == '-':
                floodFill(A,m,n,m-1,j,'-','O')
                
        for i in range(m):
            for j in range(n):
                if "-" == A[i][j]:
                    A[i][j] = 'X'
```