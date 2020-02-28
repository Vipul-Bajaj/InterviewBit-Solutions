<h1>3 Sum Zero</h1>

<p>Given an array S of n integers, are there elements a, b, c in S such that a + b + c = 0?
Find all unique triplets in the array which gives the sum of zero.

Note:

    Elements in a triplet (a,b,c) must be in non-descending order. (ie, a ≤ b ≤ c)
    The solution set must not contain duplicate triplets. For example, given array S = {-1 0 1 2 -1 -4}, A solution set is:
    (-1, 0, 1)
    (-1, -1, 2)
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return a list of list of integers
    def threeSum(self, A):
        A.sort()
        n = len(A)
        solutions = set()
        for i in range(n-2):
            j,k = i+1,n-1
            while j<k:
                s = A[i]+A[j]+A[k]
                if s == 0:
                    solutions.add((A[i],A[j],A[k]))
                    j+=1
                    k-=1
                else:
                    if s<0:
                        j+=1
                    else:
                        k-=1
                        
        # return sorted(solutions,key=lambda i:(i[0],i[1],i[2]))
        return list(solutions)
```