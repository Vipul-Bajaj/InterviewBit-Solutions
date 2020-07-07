<h1>Region in BinaryMatrix</h1>

<p>
Given a binary matrix A of size N x M.
Cells which contain 1 are called filled cell and cell that contain 0 are called empty cell.
Two cells are said to be connected if they are adjacent to each other horizontally, vertically, or diagonally.
If one or more filled cells are also connected, they form a region. Find the length of the largest region.

Input Format:

    First argument is a 2D binary matrix Aof size  N x M.
Output Format:

    Return a single interger denoting the length of largest region.
Constraints:

    1 <= N, M <= 10^2
    A[i][j]=0 or A[i][j]=1
Example:

    Input 1:
        A = [  [0, 0, 1, 1, 0]
                [1, 0, 1, 1, 0]
                [0, 1, 0, 0, 0]
                [0, 0, 0, 0, 1]
            ]
    Input 2:
        A = [  [1, 1, 1]
                [0, 0, 1]
            ]
    Output 1:
        6
    Output 2:
        4
    Explanation 1:
        The largest region is denoted by red color in the matrix:
            00110
            10110
            01000
            00001
    Explanation 2:
        The largest region is:
            111
            001

<h2>Solution</h2>

***

```python
import sys
sys.setrecursionlimit(100000000)
def isInRange(x,y,rows,cols):
    if x<0 or x>rows-1 or y<0 or y>cols-1:
        return False
    return True

def dfs(grid,visited,rows,cols,r,c,size):
    
    if not isInRange(r,c,rows,cols):
        return
    size[0]+=1
    visited[r][c] = 1
    
    neighbours = [[-1,0],[-1,-1],[0,-1],[1,-1],[1,0],[1,1],[0,1],[-1,1]]
    
    for neighbour in neighbours:
        if isInRange(r+neighbour[0],c+neighbour[1],rows,cols) and grid[r+neighbour[0]][c+neighbour[1]] == 1 and visited[r+neighbour[0]][c+neighbour[1]] == 0:
            dfs(grid,visited,rows,cols,r+neighbour[0],c+neighbour[1],size)
            
    # visited[r][c] = 0
            
class Solution:
    # @param A : list of strings
    # @return an integer
    def solve(self, A):
    
        m,n = len(A),len(A[0])
        max_size = 0
        size = 0
        visited = [[0 for j in range(n)]for i in range(m)]
        for i in range(m):
            for j in range(n):
                if visited[i][j] == 0 and A[i][j] == 1:
                    size = [0]
                    dfs(A,visited,m,n,i,j,size)
                    max_size = max(max_size,size[0])
        return max_size
```