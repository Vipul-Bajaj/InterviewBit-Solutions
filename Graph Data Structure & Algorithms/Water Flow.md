<h1>Water Flow</h1>

<p>
Given an N x M matrix A of non-negative integers representing the height of each unit cell in a continent, the "Blue lake" touches the left and top edges of the matrix and the "Red lake" touches the right and bottom edges.

Water can only flow in four directions (up, down, left, or right) from a cell to another one with height equal or lower.

Find the number of cells from where water can flow to both the Blue and Red lake.

Problem Constraints

    1 <= M, N <= 1000
    1 <= A[i][j] <= 10^9

Input Format:

    First and only argument is a 2D matrix A.

Output Format:

    Return an integer denoting the number of cells from where water can flow to both the Blue and Red lake.

Example:

    Input 1:
        A = [
                [1, 2, 2, 3, 5]
                [3, 2, 3, 4, 4]
                [2, 4, 5, 3, 1]
                [6, 7, 1, 4, 5]
                [5, 1, 1, 2, 4]
            ]
    Input 2:
        A = [
                [2, 2]
                [2, 2]
            ]
    Output 1:
        7
    Output 2:
        4
    Explanation 1:
        Blue Lake  ~   ~   ~   ~   ~ 
                ~  1   2   2   3  (5) *
                ~  3   2   3  (4) (4) *
                ~  2   4  (5)  3   1  *
                ~ (6) (7)  1   4   5  *
                ~ (5)  1   1   2   4  *
                   *   *   *   *   * Red Lake
        Water can flow to both lakes from the cells denoted in parentheses.
    Explanation 2:
        Water can flow from all cells.

<h2>Solution</h2>

***

```python
import sys 
sys.setrecursionlimit(100000000)  
def dfs(i,j,m,n,A,visited):
    if i<0 or i>=m or j<0 or j>=n:
        return
    
    visited[i][j] = True
    
    if i+1<m and A[i][j]<=A[i+1][j] and not visited[i+1][j]:
        dfs(i+1,j,m,n,A,visited)
    
    if j+1<n and A[i][j]<=A[i][j+1] and not visited[i][j+1]:
        dfs(i,j+1,m,n,A,visited)

    if i-1>=0 and A[i][j]<=A[i-1][j] and not visited[i-1][j]:
        dfs(i-1,j,m,n,A,visited)

    if j-1>=0 and A[i][j]<=A[i][j-1] and not visited[i][j-1]:
        dfs(i,j-1,m,n,A,visited)
    
    return
class Solution:
    # @param A : list of list of integers
    # @return an integer
    def solve(self, A):
        m = len(A)
    
        if m == 0:
            return 0
            
        n = len(A[0])
        ans = 0
        visited_red = [[False for j in range(n)] for i in range(m)]
        visited_blue = [[False for j in range(n)] for i in range(m)]
        
        for i in range(m):
            dfs(i,0,m,n,A,visited_blue)
        
        for i in range(n):
            dfs(0,i,m,n,A,visited_blue)
        
        for i in range(m):
            dfs(i,n-1,m,n,A,visited_red)
        
        for i in range(n):
            dfs(m-1,i,m,n,A,visited_red)
            
        for i in range(m):
            for j in range(n):
                if visited_red[i][j] and visited_blue[i][j]:
                    ans+=1
                    
        return ans

```