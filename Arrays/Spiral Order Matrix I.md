<h1>Spiral Order Matrix I</h1>

<p>Given a matrix of m * n elements (m rows, n columns), return all elements of the matrix in spiral order.</p>

<p>
<b>Example :</b>
<br>
Given the following matrix:

    [
        [ 1, 2, 3 ],
        [ 4, 5, 6 ],
        [ 7, 8, 9 ]
    ]
<br>
You should return

    [1, 2, 3, 6, 9, 8, 7, 4, 5]
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of list of integers
    # @return a list of integers
    def spiralOrder(self, A):
        m,n = len(A),len(A[0])
        t,l,b,r = 0,0,m,n
        d = 0
        res = []
        while t<b and l<r:
            if d == 0:
                for i in range(l,r):
                    res.append(A[t][i])
                    
                d=1
                t+=1
            elif d == 1:
                for i in range(t,b):
                    res.append(A[i][r-1])
                    
                d=2
                r-=1
            elif d == 2:
                for i in range(r-1,l-1,-1):
                    res.append(A[b-1][i])
                    
                d=3
                b-=1
            elif d==3:
                for i in range(b-1,t-1,-1):
                    res.append(A[i][l])
                d=0
                l+=1
                
        return res
```