<h1>Next Permutation</h1>

<p>
Implement the next permutation, which rearranges numbers into the numerically next greater permutation of numbers for a given array A of size N.

If such arrangement is not possible, it must be rearranged as the lowest possible order i.e., sorted in an ascending order.</p>

<p>
<b>Example :</b>
<br>

    Input 1:
        A = [1, 2, 3]

    Output 1:
        [1, 3, 2]

    Input 2:
        A = [3, 2, 1]

    Output 2:
        [1, 2, 3]

    Input 3:
        A = [1, 1, 5]

    Output 3:
        [1, 5, 1]

    Input 4:
        A = [20, 50, 113]

    Output 4:
        [20, 113, 50]
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return a list of integers
    def nextPermutation(self, A):
        n = len(A)
        i = n-1
        while i>0 and A[i-1]>=A[i]:
            i-=1
        if i<=0:
            return A[::-1]
            
        j = n-1
        
        while A[j]<= A[i-1]:
            j-=1
            
        A[i-1],A[j] = A[j],A[i-1]
        
        A[i : ] = A[n - 1 : i - 1 : -1]
        
        return A
        
```