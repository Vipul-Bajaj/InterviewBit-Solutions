<h1>Min Sum Path in Triangle</h1>

<p>
Given a triangle, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.

For example, given the following triangle

    [
            [2],
           [3,4],
          [6,5,7],
         [4,1,8,3]
    ]
The minimum path sum from top to bottom is 11 (i.e., 2 + 3 + 5 + 1 = 11).

    Note:
    Bonus point if you are able to do this using only O(n) extra space, where n is the total number of rows in the triangle

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @return an integer
    def minimumTotal(self, A):
        m = len(A)
    
        if m<1:
            return 0
        
        for i in range(m-2,-1,-1):
            for j in range(len(A[i])):
                A[i][j] += min(A[i+1][j],A[i+1][j+1])
        
        return A[0][0]
```