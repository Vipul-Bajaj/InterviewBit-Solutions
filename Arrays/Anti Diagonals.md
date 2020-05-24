<h1>Anti Diagonals</h1>

<p>
Give a N*N square matrix, return an array of its anti-diagonals. Look at the example for more details.

Example:
	
    Input: 	

    1 2 3
    4 5 6
    7 8 9

    Return the following :

    [ 
        [1],
        [2, 4],
        [3, 5, 7],
        [6, 8],
        [9]
    ]


    Input : 
    1 2
    3 4

    Return the following  : 

    [
        [1],
        [2, 3],
        [4]
    ]
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @return a list of list of integers
    def diagonal(self, A):
        m,n = len(A),len(A[0])
        ans = []
        for k in range(m+n-1):
            res = []
            for i in range(m):
                for j in range(n):
                    if i+j==k:
                        res.append(A[i][j])
                        
            ans.append(res)
            
        return ans
```