<h1>Flip Array</h1>

<p>
Given an array of positive elements, you have to flip the sign of some of its elements such that the resultant sum of the elements of array should be minimum non-negative(as close to zero as possible). Return the minimum no. of elements whose sign needs to be flipped such that the resultant sum is minimum non-negative.

<b>Constraints:</b>
    1 <= n <= 100
    
Sum of all the elements will not exceed 10,000.

Example:

    Input 1:
        A = [15, 10, 6]
    Output 1:
        1
    Explanation 1:
        ans = 1 (Here, we will flip the sign of 15 and the resultant sum will be 1 )
    Input 2:
        A = [14, 10, 4]
    Output 2:
        1
    Explanation 2:
        ans = 1 (Here, we will flip the sign of 14 and the resultant sum will be 0)
   
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @return an integer
    def solve(self, A):
        n = len(A)
        target = sum(A)//2
        A = sorted(A)
        lookup = [[float('inf') for _ in range(n+1)]for _ in range(target+1)]
        for i in range(n+1):
            lookup[0][i] = 0
        for i in range(1, target+1):
            for j in range(1, n+1):
                if A[j-1] <= i:
                    lookup[i][j] = min(lookup[i][j-1], lookup[i-A[j-1]][j-1] + 1)
                else:
                    lookup[i][j] = lookup[i][j-1]
        res, i = None, target
        while res == None:
            if lookup[i][-1] != float('inf'):
                res = lookup[i][-1]
            i -= 1
        return res
```
