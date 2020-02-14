<h1>Painters Partition Problem</h1>

<p>
Given 2 integers A and B and an array of integars C of size N.

Element C[i] represents length of ith board.

You have to paint all N boards [C0, C1, C2, C3 … CN-1]. There are A painters available and each of them takes B units of time to paint 1 unit of board.

Calculate and return minimum time required to paint all boards under the constraints that any painter will only paint contiguous sections of board.
1. 2 painters cannot share a board to paint. That is to say, a board
cannot be painted partially by one painter, and partially by another.
2. A painter will only paint contiguous boards. Which means a
configuration where painter 1 paints board 1 and 3 but not 2 is
invalid.
Return the ans % 10000003
</p>

<p><b>Example :</b>
<br>

```python
Input 1:
    A = 2
    B = 5
    C = [1, 10]
Output 1:
    50
Explanation 1:
    Possibility 1:- same painter paints both blocks, time taken = 55units
    Possibility 2:- Painter 1 paints block 1, painter 2 paints block 2, time take = max(5, 50) = 50
    There are no other distinct ways to paint boards.
    ans = 50%10000003

Input 2:
    A = 10
    B = 1
    C = [1, 8, 11, 3]
Output 2:
    11
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @param B : integer
    # @param C : list of integers
    # @return an integer
    def paint(self, A, B, C):
        n = len(C)
        mod = 10000003
        if A>=n:
            return (max(C)*B)%mod
            
        l,h = max(C)*B , sum(C)*B
        
        while(l<h):
            mid = (l+h)//2
            
            r = 1
            cl = 0
            
            for i in range(n):
                if cl + C[i]*B <=mid:
                    cl+=C[i]*B
                else:
                    r+=1
                    cl = C[i]*B
                    
            if r<=A:
                h=mid
            else:
                l=mid+1
                
        return l%mod
```