<h1>3 Sum</h1>

<p>Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target.
Return the sum of the three integers.

Assume that there will only be one solution

Example:
given array S = {-1 2 1 -4},
and target = 1.

The sum that is closest to the target is 2. (-1 + 2 + 1 = 2)</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return an integer
    def threeSumClosest(self, A, B):
        A.sort()
        n = len(A)
        min_diff = 2**31
        ans = None
        for i in range(n-2):
            j,k = i+1,n-1
            while j<k:
                s = A[i]+A[j]+A[k]
                if s == B:
                    return s
                else:
                    if abs(B-s)<min_diff:
                        min_diff = abs(B-s)
                        ans = s
                    if s<B:
                        j+=1
                    else:
                        k-=1
                        
        return ans
```