<h1>Sort By Color</h1>

<p>Given an array with n objects colored red, white or blue,
sort them so that objects of the same color are adjacent, with the colors in the order red, white and blue.

Here, we will use the integers 0, 1, and 2 to represent the color red, white, and blue respectively.

Note: Using library sort function is not allowed.

<p><b>Example :</b><br>Input : [0 1 2 0 1 2]<br>Modify array so that it becomes : [0 0 1 1 2 2]</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return A after the sort
    def sortColors(self, A):
        n = len(A)
        l,m = 0,0
        h = n-1
        
        while m<=h:
            if A[m]==0:
                A[l],A[m] = A[m],A[l]
                m+=1
                l+=1
            elif A[m]==1:
                m+=1
            else:
                A[m],A[h]=A[h],A[m]
                h-=1
                
        return A
```