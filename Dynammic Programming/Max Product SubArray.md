<h1>Max Product SubArray</h1>

<p>
Find the contiguous subarray within an array (containing at least one number) which has the largest product.
Return an integer corresponding to the maximum product possible.

Examples:

    Input : [2, 3, -2, 4]
    Return : 6 

    Possible with [2, 3]

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @return an integer
    def maxProduct(self, A):
        n = len(A)
        minVal = A[0] 
        maxVal = A[0] 
      
        maxProduct = A[0] 
      
        for i in range(1, n): 
            if (A[i] < 0): 
                temp = maxVal 
                maxVal = minVal 
                minVal = temp 
    
            maxVal = max(A[i], maxVal * A[i]) 
            minVal = min(A[i], minVal * A[i]) 
      
            maxProduct = max(maxProduct, maxVal) 
      
        return maxProduct 
```