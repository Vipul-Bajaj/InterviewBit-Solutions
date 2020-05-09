<h1>Word Search Board</h1>

<p>
Given a 2D board and a word, find if the word exists in the grid.

The word can be constructed from letters of sequentially adjacent cell, where "adjacent" cells are those horizontally or vertically neighboring. The cell itself does not count as an adjacent cell.
The same letter cell may be used more than once.

Example :

    Given board =

    [
        ["ABCE"],
        ["SFCS"],
        ["ADEE"]
    ]

    word = "ABCCED", -> returns 1,
    word = "SEE", -> returns 1,
    word = "ABCB", -> returns 1,
    word = "ABFSAB" -> returns 1
    word = "ABCD" -> returns 0
    Note that 1 corresponds to true, and 0 corresponds to false.

<h2>Solution</h2>

***

```python
def find(mat, pat, rows,col,i,j,level):
    
    l = len(pat)
    if l == level:
        return True
        
    if i < 0 or j < 0 or i >= rows or j >= col: 
        return False
        
    if mat[i][j] == pat[level]:
  
        temp = mat[i][j] 
  
        res = find(mat, pat,  rows, col,i-1, j, level + 1) or find(mat, pat,  rows, col,i+1, j, level + 1) or find(mat, pat, rows, col, i, j-1, level + 1) or find(mat, pat,  rows, col,i, j+1, level + 1)
  
        return res 
      
    else :
        return False
class Solution:
    # @param A : list of strings
    # @param B : string
    # @return an integer
    def exist(self, A, B):
        l = len(B)
    
        if l<1:
            return False
        m = len(A)
        n = len(A[0])
        for i in range(m):
            for j in range(n):
                if B[0] == A[i][j]:
                    if find(A,B,m,n,i,j,0):
                        return 1
                        
        return 0
```