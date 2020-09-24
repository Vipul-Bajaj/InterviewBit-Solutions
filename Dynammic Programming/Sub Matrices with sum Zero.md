<h1>Sub Matrices with sum Zero</h1>

<p>
Given a 2D matrix, find the number non-empty sub matrices, such that the sum of the elements inside the sub matrix is equal to 0. (note: elements might be negative).

Examples:

    Input : 
        -8 5  7
        3  7 -8
        5 -8  9

    Return : 2

    Explanation : 
        -8 5 7
        3 7 -8
        5 -8 9

        -8 5 7
        3 7 -8
        5 -8 9
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @return an integer
    def solve(self, A):
        ans = 0
        m = len(A)
        if m == 0:
            return 0
        n = len(A[0])
        
        for i in range(0,m):
            for j in range(1,n):
                A[i][j] += A[i][j-1]
                
        h = {}
        
        for i in range(n):
            for j in range(i,n):
                h = {}
                
                h[0] = 1
                
                s = 0
                
                for k in range(m):
                    curr = A[k][j]
                    
                    if i-1>=0:
                        curr-=A[k][i-1]
                        
                    s+=curr
                    ans+=h.get(0-s,0)
                    if -s in h:
                        h[-s]+=1
                    else:
                        h[-s]=1
        return ans
```
