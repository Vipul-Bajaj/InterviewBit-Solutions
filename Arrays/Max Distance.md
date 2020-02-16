<h1>Max Distance</h1>

<p>Given an array A of integers, find the maximum of j - i subjected to the constraint of A[i] <= A[j].
If there is no solution possible, return -1.</p>

<p>
<b>Example :</b>
<br>

    A : [3 5 4 2]
    Output : 2 
    for the pair (3, 4)
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @return an integer
    def maximumGap(self, A):
        n = len(A)
        idx = list(range(n))
        
        idx = sorted(idx,key=lambda x:A[x])
        
        max_dist = 0
    
        for i in range(n-1):
            j = i+1
            while j<n and idx[i]<=idx[j]:
                max_dist=max(max_dist,idx[j]-idx[i])
                j+=1
                
        return max_dist
```