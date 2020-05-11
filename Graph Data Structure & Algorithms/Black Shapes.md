<h1>Black Shapes</h1>

<p>
Given N x M character matrix A of O's and X's, where O = white, X = black.

Return the number of black shapes. A black shape consists of one or more adjacent X's (diagonals not included)



Input Format:

    The First and only argument is a N x M character matrix.
Output Format:

    Return a single integer denoting number of black shapes.
Constraints:

    1 <= N,M <= 1000
    A[i][j] = 'X' or 'O'
Example:

    Input 1:
        A = [ OOOXOOO
            OOXXOXO
            OXOOOXO  ]
    Output 1:
        3
    Explanation:
        3 shapes are  :
        (i)    X
             X X
        (ii)
            X
        (iii)
            X
            X
Note: we are looking for connected shapes here.

    XXX
    XXX
    XXX
    is just one single connected black shape.

<h2>Solution</h2>

***

```python
def isInRange(x,y,rows,cols):
    if x<0 or x>rows-1 or y<0 or y>cols-1:
        return False
    return True

def dfs(grid,visited,rows,cols,r,c):
    
    if not isInRange(r,c,rows,cols):
        return
    
    visited[r][c] = 1
    
    neighbours = [[0,-1],[1,0],[0,1],[-1,0]]
    
    for neighbour in neighbours:
        if isInRange(r+neighbour[0],c+neighbour[1],rows,cols) and grid[r+neighbour[0]][c+neighbour[1]] == 'X' and visited[r+neighbour[0]][c+neighbour[1]] == 0:
            dfs(grid,visited,rows,cols,r+neighbour[0],c+neighbour[1])
            
class Solution:
    # @param A : list of strings
    # @return an integer
    def black(self, A):
        count = 0
    
        m,n = len(A),len(A[0])
        
        visited = [[0 for j in range(n)]for i in range(m)]
        for i in range(m):
            for j in range(n):
                if visited[i][j] == 0 and A[i][j] == 'X':
                    count+=1
                    dfs(A,visited,m,n,i,j)
        
        return count
```