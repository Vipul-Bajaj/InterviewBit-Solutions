<h1>NQueens</h1>

<p>
The n-queens puzzle is the problem of placing n queens on an n×n chessboard such that no two queens attack each other.

<img src="http://i.imgur.com/yaxpgda.png">

Given an integer n, return all distinct solutions to the n-queens puzzle.

Each solution contains a distinct board configuration of the n-queens’ placement, where 'Q' and '.' both indicate a queen and an empty space respectively.

For example,
There exist two distinct solutions to the 4-queens puzzle:

    [
    [".Q..",  // Solution 1
    "...Q",
    "Q...",
    "..Q."],

    ["..Q.",  // Solution 2
    "Q...",
    "...Q",
    ".Q.."]
    ]
    
</p>

<h2>Solution</h2>

***

```python
def isSafe(board,m,n,row,col):
    for i in range(m):
        if board[i][col] == 'Q' and i!=row:
            return False
    for i in range(n):
        if board[row][i] == 'Q' and i!=col:
            return False
    
    i,j = row+1,col+1
    
    while i<m and j<n:
        if board[i][j] == 'Q':
            return False
        i+=1
        j+=1
        
    i,j = row-1,col-1
    
    while i>=0 and j>=0:
        if board[i][j] == 'Q':
            return False
        i-=1
        j-=1
    
    i,j = row-1,col+1
    
    while i>=0 and j<n:
        if board[i][j] == 'Q':
            return False
        i-=1
        j+=1
        
    i,j = row+1,col-1
    
    while i<m and j>=0:
        if board[i][j] == 'Q':
            return False
        i+=1
        j-=1
            
    return True
    
def solve(A,board,res,col):
    if col>=A:
        res.append(["".join(b) for b in board])
        return True
    r = False
    for i in range(A):
        if isSafe(board,A,A,i,col):
            board[i][col] = 'Q'
            r = solve(A,board,res,col+1) or r
            board[i][col] = '.'
    return r
class Solution:
    # @param A : integer
    # @return a list of list of strings
    def solveNQueens(self, A):
        board = [['.' for j in range(A)]for i in range(A)]
        res = []
        solve(A,board,res,0)
        return res
```