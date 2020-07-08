<h1>Min Cost Path</h1>

<p>
You are given a AB character matrix named C. Every cell in C has a character U,R,L or D indicating up,right,left and down.

Your target is to go from top left corner to the bottom right corner of the matrix.

But there are some restrictions while moving along the matrix:

If you follow what is written in the cell then you can move freely.
But if you don't follow what is written in the cell then you have to pay 1 unit of cost.
Like: If a cell contains character U and you go right instead of Up you have to pay 1 unit of cost.

So your task is to find the minimum cost to go from top-left corner to the bottom-right corner.
Input Format:

    First Argument represents a integer A (number of rows).
    Second Argument represents a integer B (number of columns).
    Third Argument represents a string array C which contains A strings each of length B.
Output Format:

    Return an integer denoting the minimum cost to travel from top-left corner to bottom-right corner.
Constraints:

    1 <= A,B <= 10^3
    C[i][j] can be either U,R,L or D.
Example:

    Input:1
        A = 3
        B = 3
        C = ["RRR","DDD","UUU"]
    Input:2
        A = 1
        B = 4
        C = ["LLLL"]
    Output-1 :
        1
    Output-2 :
        3
    Explanation for Input-1:
        Matrix looks like:  RRR
                            DDD
                            UUU
        We go right two times and down two times.
        So from top-right cell we are going down though right is given so this incurs a cost of 1.
    Explanation for Input-2:
        Matrix looks like: LLLL
        We go right three times.

<h2>Solution</h2>

***

```python
import collections

move = [['D', 1, 0], ['U', -1, 0], ['L', 0, -1], ['R', 0, 1]]

def valid(x, y, limx, limy):
    return (0 <= x < limx and 0 <= y < limy)

class Solution:
    # @param A : integer
    # @param B : integer
    # @param C : list of strings
    # @return an integer
    def solve(self, A, B, C):
        global move
        de = collections.deque([])
        dist = [[10**18 for i in range(B)] for j in range(A)]
        dist[0][0] = 0
        de.append((0, 0))
        while de:
            node = de.popleft()
            for i in range(4):
                u = (node[0] + move[i][1], node[1] + move[i][2])
                w = (move[i][0] != C[node[0]][node[1]])
                if valid(u[0], u[1], A, B):
                    if dist[u[0]][u[1]] > dist[node[0]][node[1]] + w:
                        dist[u[0]][u[1]] = dist[node[0]][node[1]] + w
                        if w == 1:
                            de.append(u)
                        else:
                            de.appendleft(u)
        return dist[-1][-1]
```