<h1>Sorted Inserted Position</h1>

<p>
Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

Here are few examples.
</p>

<p><b>Example :</b>
<br>

```python
[1,3,5,6], 5 → 2
[1,3,5,6], 2 → 1
[1,3,5,6], 7 → 4
[1,3,5,6], 0 → 0
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return an integer
    def searchInsert(self, A, B):
        n = len(A)
    
        l,h = 0,n-1
        idx = -1
        
        while l<=h:
            mid = (l+h)//2
            
            if (A[mid] == B):
                return mid
            elif A[mid]<B:
                if mid == h and B>A[mid]:
                    return mid+1
                l = mid+1
            else:
                if mid == l and B<A[mid]:
                    return mid
                h = mid-1
                
        return n
```