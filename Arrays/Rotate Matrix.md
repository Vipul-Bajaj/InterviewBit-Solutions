<h1>Rotate Matrix</h1>

<p>You are given an n x n 2D matrix representing an image.

Rotate the image by 90 degrees (clockwise).

You need to do this in place.

Note that if you end up using an additional array, you will only receive partial score.</p>

<p>
<b>Example :</b>
<br>
If the array is

    [
        [1, 2],
        [3, 4]
    ]
<br>
Then the rotated array becomes:

    [
        [3, 1],
        [4, 2]
    ]
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @return the same list modified
    def rotate(self, A):
        m,n = len(A),len(A[0])
        
        for i in range(m):
            for j in range(i,n):
                A[i][j],A[j][i] = A[j][i],A[i][j]
                

        for i in range(m):
            A[i] = reversed(A[i])
            
        return A
```