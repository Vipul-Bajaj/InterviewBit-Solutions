<h1>All Unique Permutations</h1>

<p>Given a collection of numbers that might contain duplicates, return all possible unique permutations.

<b>Example:</b>

    [1,1,2] have the following unique permutations:

    [1,1,2]
    [1,2,1]
    [2,1,1]
    
</p>
<p>

    NOTE : No 2 entries in the permutation sequence should be the same. 
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
        def shouldSwap(string, start, curr):  
            for i in range(start, curr):  
                if string[i] == string[curr]:  
                    return False
            return True
            
        def permuteHelper(a, l, r, res):
            if l == r:
                res.append(a[::])
            for i in range(l, r + 1):
                if shouldSwap(a,l,i):
                    a[i], a[l] = a[l], a[i]
                    permuteHelper(a, l + 1, r, res)
                    a[i], a[l] = a[l], a[i]
        res = []        
        permuteHelper(A,0,len(A)-1,res)
        return res
```