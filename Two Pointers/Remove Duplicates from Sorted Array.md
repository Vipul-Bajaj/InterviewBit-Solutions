<h1>Remove Duplicates from Sorted Array</h1>

<p>Remove duplicates from Sorted Array
Given a sorted array, remove the duplicates in place such that each element appears only once and return the new length.

Note that even though we want you to return the new length, make sure to change the original array as well in place

Do not allocate extra space for another array, you must do this in place with constant memory.</p>

<p><b>Example :</b><br>Input : [1 1 2 2 3]<br>Modify array so that it becomes : [1 2 3] and return length of modified array i.e. 3</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def removeDuplicates(self, A):
        n = len(A)
    
        if n<2:
            return n
        
        i,j=0,1
        
        while j<n:
            if A[i]==A[j]:
                j+=1
            else:
                A[i+1],A[j]=A[j],A[i+1]
                j+=1
                i+=1
                
        A = A[:i+1]
        return len(A)
```