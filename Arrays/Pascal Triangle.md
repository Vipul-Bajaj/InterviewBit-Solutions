<h1>Pascal Triangle</h1>

<p>
Given numRows, generate the first numRows of Pascal’s triangle.

Pascal’s triangle : To generate A[C] in row R, sum up A’[C] and A’[C-1] from previous row R - 1.

Example:

    Given numRows = 5,

    Return

    [
        [1],
        [1,1],
        [1,2,1],
        [1,3,3,1],
        [1,4,6,4,1]
    ]
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return a list of list of integers
    def solve(self, A):
        n = A
        
        pascal = []
        
        for r in range(1,n+1):
            res = 1
            pascal_row = []
            for i in range(1,r+1):
                pascal_row.append(res)
                res*=(r-i)
                res//=(i)
                
                
            pascal.append(pascal_row)
            
        return pascal
```