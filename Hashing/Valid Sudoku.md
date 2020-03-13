<h1>Valid Sudoku</h1>

<p>
Determine if a Sudoku is valid, according to: http://sudoku.com.au/TheRules.aspx

The Sudoku board could be partially filled, where empty cells are filled with the character ‘.’.

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png">

The input corresponding to the above configuration :
    
    ["53..7....", "6..195...", ".98....6.", "8...6...3", "4..8.3..1", "7...2...6", ".6....28.", "...419..5", "....8..79"]

A partially filled sudoku which is valid.

    1. A valid Sudoku board (partially filled) is not necessarily solvable. Only the filled cells need to be validated.

Return 0 / 1 ( 0 for false, 1 for true ) for this problem
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of strings
    # @return an integer
    def isValidSudoku(self, A):
        n = len(A)
        for k in range(0,n,3):
            
            h = {}
            for i in range(k,k+3):
                for j in range(3):
                    if A[i][j] in h and A[i][j] != '.':
                        return 0
                    else:
                        h[A[i][j]]=1
                   
            h = {} 
            for i in range(k,k+3):
                for j in range(3,6):
                    if A[i][j] in h and A[i][j] != '.':
                        return 0
                    else:
                        h[A[i][j]]=1
            
            h = {}        
            for i in range(k,k+3):
                for j in range(6,9):
                    if A[i][j] in h and A[i][j] != '.':
                        return 0
                    else:
                        h[A[i][j]]=1
                
        for i in range(n):
            h = {}
            for j in range(n):
                if A[i][j] in h and A[i][j] != '.':
                    return 0
                else:
                    h[A[i][j]]=1
                    
        for i in range(n):
            h = {}
            for j in range(n):
                if A[j][i] in h and A[j][i] != '.':
                    return 0
                else:
                    h[A[j][i]]=1
                    
        return 1
```