<h1>Permutations</h1>

<p>Given a collection of numbers, return all possible permutations.

<b>Example:</b>

    [1,2,3] will have the following permutations:

    [1,2,3]
    [1,3,2]
    [2,1,3] 
    [2,3,1] 
    [3,1,2] 
    [3,2,1]
    
</p>
<p>

    NOTE
    1. No two entries in the permutation sequence should be the same.
    2. For the purpose of this problem, assume that all the numbers in the collection are unique.
</p>
<p>

    Warning : DO NOT USE LIBRARY FUNCTION FOR GENERATING PERMUTATIONS.
    Example : next_permutations in C++ / itertools.permutations in python.
    If you do, we will disqualify your submission retroactively and give you penalty points.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return a list of list of integers
    def permute(self, A):
        res = []
        def permute(a, l, r): 
            if l==r: 
                res.append(a.copy())
            else: 
                for i in range(l,r+1): 
                    a[l], a[i] = a[i], a[l] 
                    permute(a, l+1, r) 
                    a[l], a[i] = a[i], a[l] # backtrack 
        permute(A,0,len(A)-1)
        return res
```