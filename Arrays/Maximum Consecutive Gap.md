<h1>Maximum Consecutive Gap</h1>

<p>Given an unsorted array, find the maximum difference between the successive elements in its sorted form.

Try to solve it in linear time/space.

Example :

    Input : [1, 10, 5]
    Output : 5 
Return 0 if the array contains less than 2 elements.

You may assume that all the elements in the array are non-negative integers and fit in the 32-bit signed integer range.
You may also assume that the difference will not overflow.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @return an integer
    def maximumGap(self, A):
        n = len(A)
        if n<2:
            return 0

        A = sorted(A)
        
        max_diff = 0
        
        for i in range(n-1):
            max_diff = max(max_diff,A[i+1]-A[i])
            
        return max_diff
```