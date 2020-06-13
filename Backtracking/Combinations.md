<h1>Permutations</h1>

<p>
Given two integers n and k, return all possible combinations of k numbers out of 1 2 3 ... n.

Make sure the combinations are sorted.

To elaborate,
1. Within every entry, elements should be sorted. [1, 4] is a valid entry while [4, 1] is not.
2. Entries should be sorted within themselves.

Example :
    If n = 4 and k = 2, a solution is:

    [
        [1,2],
        [1,3],
        [1,4],
        [2,3],
        [2,4],
        [3,4],
    ]

Warning : DO NOT USE LIBRARY FUNCTION FOR GENERATING COMBINATIONS.
Example : itertools.combinations in python.
If you do, we will disqualify your submission retroactively and give you penalty points. 
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @param B : integer
    # @return a list of list of integers
    def combine(self, A, B):
        A = list(range(1,A+1))
        def combinations(lst,n):
            if n == 0: 
                return [[]] 
              
            l =[] 
            for i in range(0, len(lst)): 
                  
                m = lst[i] 
                remLst = lst[i + 1:] 
                  
                for p in combinations(remLst, n-1): 
                    l.append([m]+p) 
                      
            return l
            
        return sorted(combinations(A,B))
```