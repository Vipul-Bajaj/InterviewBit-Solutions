<h1>Minimize the Absolute Difference</h1>

<p>Given three sorted arrays A, B and Cof not necessarily same sizes.

Calculate the minimum absolute difference between the maximum and minimum number from the triplet a, b, c such that a, b, c belongs arrays A, B, C respectively.
i.e. minimize | max(a,b,c) - min(a,b,c) |.</p>

<p><b>Example :</b>
<br>
Input : 

    A : [ 1, 4, 5, 8, 10 ]
    B : [ 6, 9, 15 ]
    C : [ 2, 3, 6, 6 ]
<br>
Output : 

    1
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : list of integers
    # @param C : list of integers
    # @return an integer
    def solve(self, A, B, C):
        m,n,o = len(A),len(B),len(C)
    
        i,j,k=0,0,0
        min_diff = 2**31-1
        while i<m and j<n and k<o:
            min_diff = min(max(A[i],B[j],C[k])-min(A[i],B[j],C[k]),min_diff)
            
            _min = min(A[i],B[j],C[k])
            
            if _min == A[i]:
                i+=1
            elif _min == B[j]:
                j+=1
            else:
                k+=1
            
        return min_diff
```