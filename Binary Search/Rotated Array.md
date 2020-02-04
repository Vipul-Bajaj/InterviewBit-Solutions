<h1>Rotated Array</h1>

<p>Suppose a sorted array A is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

Find the minimum element.

The array will not contain duplicates.</p>

<p><b>Example :</b>
<br>
A = [4 5 6 7 0 1 2]
<br>
Return 0
</p>

<h2>Solution</h2>

***

```python
def get_minimum_from_sorted_rotated_array(arr,n):
    low = 0
    high = n-1
    while low<=high:
        if arr[low]<=arr[high]:
            return low
        mid = (low+high)//2
        prev = (n+mid-1)%n
        nxt = (mid+1)%n
        if arr[mid]<=arr[nxt] and arr[mid]<=arr[prev]:
            return mid
        elif arr[mid]<=arr[high]:
            high = mid - 1
        else:
            low = mid + 1
            
    return -1
class Solution:
    # @param A : tuple of integers
    # @return an integer
    def findMin(self, A):
        return A[get_minimum_from_sorted_rotated_array(A,len(A))]V
```