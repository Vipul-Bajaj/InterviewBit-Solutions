<h1>Matrix Search</h1>

<p>SGiven a matrix of integers A of size N x M and an integer B.

Write an efficient algorithm that searches for integar B in matrix A.

This matrix A has the following properties:

Integers in each row are sorted from left to right.
1. The first integer of each row is greater than or equal to the last integer of the previous row.
2. Return 1 if B is present in A, else return 0.

Note: Rows are numbered from top to bottom and columns are numbered from left to right.</p>

<p><b>For Example :</b>
<br>

```python
Input 1:
    A = 
    [ [1,   3,  5,  7],
      [10, 11, 16, 20],
      [23, 30, 34, 50]  ]
    B = 3
Output 1:
    1

Input 2:
    A = [   [5, 17, 100, 111]
            [119, 120,  127,   131]    ]
    B = 3
Output 2:
    0
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @param B : integer
    # @return an integer
    def searchMatrix(self, A, B):
        m,n = len(A),len(A[0])
    
        for i in range(m):
            if A[i][0]<=B<=A[i][n-1]:
                l,h = 0,n-1
                while l<=h:
                    mid = (l+h)//2
                    if A[i][mid]==B:
                        return 1
                    elif B<A[i][mid]:
                        h=mid-1
                    else:
                        l=mid+1
                return 0
        
        return 0
```