<h1>Diffk II</h1>

<p>Given an array A of integers and another non negative integer k, find if there exists 2 indices i and j such that A[i] - A[j] = k, i != j.</p>

<p><b>Example :</b>
<br>

    Input: 
        A : [1 5 3]
        k : 2
    Output: 
        1
        as 3 - 1 = 2

Return 0 / 1 for this problem.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @param B : integer
    # @return an integer
    def diffPossible(self, A, B):
        
        for i,ele in enumerate(A):
            if abs(ele+B) in A and A.index(ele+B) != i:
                return 1
                
        return 0
```