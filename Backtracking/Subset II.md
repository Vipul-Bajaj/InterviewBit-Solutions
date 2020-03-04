<h1>Subset II</h1>

<p>
Given a collection of integers that might contain duplicates, S, return all possible subsets.

    Note:
    1. Elements in a subset must be in non-descending order.
    2. The solution set must not contain duplicate subsets.
    3. Also, the subsets should be sorted in ascending ( lexicographic ) order.

<b>Example:</b>

    If S = [1,2,2], a solution is:

    [
        [],
        [1],
        [1,2],
        [1,2,2],
        [2],
        [2, 2]
    ]
    
</p>

<h2>Solution</h2>

***

```python
def solve(A,res,st):
    if len(A) == 0:
        return res
    for i in range(len(A)):
        st.append(A[i])
        a = sorted(st[:])
        if a not in res:
            res.append(a)
        solve(A[i+1:],res,st)
        st.pop(-1)
    return res
class Solution:
    # @param A : list of integers
    # @return a list of list of integers
    def subsetsWithDup(self, A):
        res = solve(A,[[]],[])    
        res.sort()
        return res
```