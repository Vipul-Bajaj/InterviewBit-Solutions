<h1>Queen Attack</h1>

<p>
On a N * M chessboard, where rows are numbered from 1 to N and columns from 1 to M, there are queens at some cells. Return a N * M array A, where A[i][j] is number of queens that can attack cell (i, j). While calculating answer for cell (i, j), assume there is no queen at that cell.

Notes:

1. Queen is able to move any number of squares vertically, horizontally or diagonally on a chessboard. A queen cannot jump over another queen to attack a position.
2. You are given an array of N strings, each of size M. Each character is either a 1 or 0 denoting if there is a queen at that position or not, respectively.
3. Expected time complexity is worst case O(N*M).

<b>For example:</b>

    Let chessboard be,
    [0 1 0]
    [1 0 0]
    [0 0 1]

    where a 1 denotes a queen at that position.

    Cell (1, 1) is attacked by queens at (2, 1), (1,2) and (3,3).
    Cell (1, 2) is attacked by queen at (2, 1). Note that while calculating this, we assume that there is no queen at (1, 2).
    Cell (1, 3) is attacked by queens at (3, 3) and (1, 2).
    and so on...

    Finally, we return matrix
    [3, 1, 2]
    [1, 3, 3]
    [2, 3, 0]
</p>

<h2>Solution</h2>

***

```python
class Solution:
	# @param A : list of strings
	# @return a list of list of integers
	def queenAttack(self, A):
        dp=[[0 for i in range(len(A[0]))] for j in range(len(A))]
        directions=[[-1,-1],[-1,0],[-1,1],[0,1],[1,1],[1,0],[1,-1],[0,-1]]
        for i in range(len(dp)):
            for j in range(len(dp[0])):
                if A[i][j]=="0":
                    continue
                for k in directions:
                    x,y=i+k[0],j+k[1]
                    while (x>=0 and x<len(A) )and( y>=0 and y<len(A[0])):
                        dp[x][y]+=1
                        if A[x][y]=="1":
                            break
                        x,y=x+k[0],y+k[1]
        return dp
```
