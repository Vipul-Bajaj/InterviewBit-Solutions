<h1>Remove Duplicates from Sorted Array</h1>

<p>Given an array and a value, remove all the instances of that value in the array.
Also return the number of elements left in the array after the operation.
It does not matter what is left beyond the expected length</p>

<p><b>Example :</b>
<br>
Input Array A : [4 1 1 2 1 3] and element B = 1
<br>
The returned length should be 3 and array should become [4 2 3 1 1 1]</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return an integer
    def removeElement(self, A, B):
        n = len(A)
    
        i,j=0,0
        
        while j<n:
            if A[j] == B:
                j+=1
            else:
                A[i],A[j] = A[j],A[i]
                i+=1
                j+=1
    
        return i
```