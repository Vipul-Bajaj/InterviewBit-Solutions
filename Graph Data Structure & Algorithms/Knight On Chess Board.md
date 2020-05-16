<h1>Knight On Chess Board</h1>

<p>
Given any source point, (C, D) and destination point, (E, F) on a chess board, we need to find whether Knight can move to the destination or not.

<img src="https://i.imgur.com/lmKL4AU.jpg">

The above figure details the movements for a knight ( 8 possibilities ).

If yes, then what would be the minimum number of steps for the knight to move to the said point.
If knight can not move from the source point to the destination point, then return -1.

Note: A knight cannot go out of the board.


Input Format

    The first argument of input contains an integer A.
    The second argument of input contains an integer B.
        => The chessboard is of size A x B.
    The third argument of input contains an integer C.
    The fourth argument of input contains an integer D.
        => The Knight is initially at position (C, D).
    The fifth argument of input contains an integer E.
    The sixth argument of input contains an integer F.
        => The Knight wants to reach position (E, F).
Output Format

    If it is possible to reach the destination point, return the minimum number of moves.
    Else return -1.
Constraints

    1 <= A, B <= 500
For Example

    Input 1:
        A = 8
        B = 8
        C = 1
        D = 1
        E = 8
        F = 8
        
    Output 1:
        6

    Explanation 1:
        The size of the chessboard is 8x8, the knight is initially at (1, 1) and the knight wants to reach position (8, 8).
        The minimum number of moves required for this is 6.

<h2>Solution</h2>

***

```python
from collections import deque
class Solution:
    # @param A : integer
    # @param B : integer
    # @param C : integer
    # @param D : integer
    # @param E : integer
    # @param F : integer
    # @return an integer
    def knight(self, A, B, C, D, E, F):
        i,j=C-1,D-1
        queue=deque([((i,j),0)])
        
        final=set()
        final.add((i,j))
        while(bool(queue)):
            pre=queue.pop()
            i,j=pre[0][0],pre[0][1]
            dist=pre[1]
            
            if (i,j)==(E-1,F-1):
                return dist
            
            xarr=[-1,-2,-2,-1,1,2,2,1]
            yarr=[-2,-1,1,2,2,1,-1,-2]
            
            for k in range(8):
                x,y=i+xarr[k],j+yarr[k]
                if(x>=0 and x<A and y>=0 and y<B):
                    if((x,y) not in final):
                        final.add((x,y))
                        queue.appendleft(((x,y),dist+1))
            
        
        return -1
```