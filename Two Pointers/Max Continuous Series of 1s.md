<h1>Max Continuous Series of 1s</h1>

<p>
You are given with an array of 1s and 0s. And you are given with an integer M, which signifies number of flips allowed.
Find the position of zeros which when flipped will produce maximum continuous series of 1s.

For this problem, return the indices of maximum continuous series of 1s in order.

Example:

    Input : 
    Array = {1 1 0 1 1 0 0 1 1 1 } 
    M = 1

    Output : 
    [0, 1, 2, 3, 4] 

If there are multiple possible solutions, return the sequence which has the minimum start index.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return a list of integers
    def maxone(self, A, B):
        n = len(A)
        left = 0
        count = 0
        window = 0
        
        leftIndex = 0
        
        for right in range(n):
            if A[right] == 0:
                count = count + 1
            while count > B:
                if A[left] == 0:
                    count = count - 1
                left = left + 1
            if right - left + 1 > window:
                window = right - left + 1
                leftIndex = left
        
        return list(range(leftIndex,window+leftIndex))s
```