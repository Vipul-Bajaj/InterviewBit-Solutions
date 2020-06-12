<h1>Largest Continuous Sequence Zero Sum</h1>

<p>
Find the largest continuous sequence in a array which sums to zero.

Example:

    Input:  {1 ,2 ,-2 ,4 ,-4}
    Output: {2 ,-2 ,4 ,-4}

NOTE : If there are multiple correct answers, return the sequence which occurs first in the array. 
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return a list of integers
    def lszero(self, A):
        n = len(A)
        k=l=0
        ps = 0
        prefix = {
            0:-1
        }
        for i in range(n):
            ps += A[i]
            if ps in prefix:
                if(i-prefix[ps]>l-k):
                    k=prefix[ps]
                    l=i
            else:
                prefix[ps]=i
    
        return A[k+1:l+1]
```