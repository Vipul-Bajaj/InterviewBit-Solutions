<h1>Kth Row of Pascal's Triangle</h1>

<p>
Given an index k, return the kth row of the Pascal’s triangle.

Pascal’s triangle : To generate A[C] in row R, sum up A’[C] and A’[C-1] from previous row R - 1.

Example:

    Input : k = 3

    Return : [1,3,3,1]
    
NOTE : k is 0 based. k = 0, corresponds to the row [1]. 
Note:Could you optimize your algorithm to use only O(k) extra space?
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return a list of integers
    def getRow(self, A):
        n = A
        
        pascal_row = []

        res=1
        for i in range(0,n+1):
            pascal_row.append(res)
            res*=(n-i)
            res//=(i+1)
            
        return pascal_row
```