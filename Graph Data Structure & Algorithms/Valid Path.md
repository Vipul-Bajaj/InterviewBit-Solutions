<h1>Valid Path</h1>

<p>
There is a rectangle with left bottom as  (0, 0) and right up as (x, y). There are N circles such that their centers are inside the rectangle.
Radius of each circle is R. Now we need to find out if it is possible that we can move from (0, 0) to (x, y) without touching any circle.

Note : We can move from any cell to any of its 8 adjecent neighbours and we cannot move outside the boundary of the rectangle at any point of time.


Input Format

    1st argument given is an Integer x.
    2nd argument given is an Integer y.
    3rd argument given is an Integer N, number of circles.
    4th argument given is an Integer R, radius of each circle.
    5th argument given is an Array A of size N, where A[i] = x cordinate of ith circle
    6th argument given is an Array B of size N, where B[i] = y cordinate of ith circle
Output Format

    Return YES or NO depending on weather it is possible to reach cell (x,y) or not starting from (0,0).
Constraints

    0 <= x, y, R <= 100
    1 <= N <= 1000
    Center of each circle would lie within the grid
For Example

    Input:
        x = 2
        y = 3
        N = 1
        R = 1
        A = [2]
        B = [3]
    Output:
        NO
    
    Explanation:
        There is NO valid path in this case

<h2>Solution</h2>

***

```python
import math
class Solution:
    # @param A : integer
    # @param B : integer
    # @param C : integer
    # @param D : integer
    # @param E : list of integers
    # @param F : list of integers
    # @return a strings
    def solve(self, A, B, C, D, E, F):
        mat = [[0 for j in range(B+1)]for i in range(A+1)]
    
        for i in range(A+1):
            for j in range(B+1):
                for k in range(C):
                    if (math.sqrt((pow((E[k] - i), 2) + pow((F[k] - j), 2))) <= D): 
                        mat[i][j] = -1
        
        # print(mat)                
        if (mat[0][0] == -1) or mat[A][B] == -1:  
            return "NO"
    
        qu = []
      
        mat[0][0] = 1
        qu.append([0, 0])  
        
        neighbours = [[-1,-1],[-1,0],[-1,1],[0,-1],[0,1],[1,-1],[1,0],[1,1]]
        while qu:
            ele = qu.pop(0)
            
            for neighbour in neighbours:
                x = ele[0] + neighbour[0]
                y = ele[1] + neighbour[1]
                
                if x<0 or x>A or y<0 or y>B:
                    continue
                
                if mat[x][y] == 0:
                    mat[x][y] = 1
                    qu.append([x,y])
        
        return "YES" if mat[A][B] else "NO"
```