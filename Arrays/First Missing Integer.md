<h1>First Missing Integer</h1>

<p>Given an unsorted integer array, find the first missing positive integer.

Example:

Given [1,2,0] return 3,

[3,4,-1,1] return 2,

[-8, -7, -6] returns 1

Your algorithm should run in O(n) time and use constant space.</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def firstMissingPositive(self, A):
        n = len(A)
        i=0
        while i<n:
            if 1<=A[i] and A[i]<=n:
                pos = A[i]-1
                if A[pos]!=A[i]:
                    A[i],A[pos] = A[pos],A[i]
                    i-=1
            i+=1
                
        for i in range(n):
            if A[i] != i+1:
                return (i+1)
                
        return (n+1)
```