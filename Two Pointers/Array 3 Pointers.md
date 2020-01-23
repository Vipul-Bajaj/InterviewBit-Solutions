<h1>Array 3 Pointers</h1>

<p>You are given 3 arrays A, B and C. All 3 of the arrays are sorted.

Find i, j, k such that :
max(abs(A[i] - B[j]), abs(B[j] - C[k]), abs(C[k] - A[i])) is minimized.
Return the minimum max(abs(A[i] - B[j]), abs(B[j] - C[k]), abs(C[k] - A[i]))</p>

<p><b>Example :</b>
<br>
Input : 
        A : [1, 4, 10]
        B : [2, 15, 20]
        C : [10, 12]
<br>
Output : 5 
         With 10 from A, 15 from B and 10 from C.</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @param B : tuple of integers
    # @param C : tuple of integers
    # @return an integer
    def minimize(self, A, B, C):
        i = len(A) - 1
        j = len(B) - 1
        k = len(C) - 1
    
        min_diff = abs(max(A[i], B[j], C[k]) -
        min(A[i], B[j], C[k])) 
    
        while i != -1 and j != -1 and k != -1: 
            current_diff = abs(max(A[i], B[j],  
            C[k]) - min(A[i], B[j], C[k])) 
    
            if current_diff < min_diff: 
                min_diff = current_diff 
    
            max_term = max(A[i], B[j], C[k]) 
    
            if A[i] == max_term: 
                i -= 1
            elif B[j] == max_term: 
                j -= 1
            else: 
                k -= 1
        return min_diff 
```