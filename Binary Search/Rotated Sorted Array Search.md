<h1>Rotated Sorted Array Search</h1>

<p>Given an array of integers A of size N and an integer B.

array A is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2 ).

You are given a target value B to search. If found in the array, return its index, otherwise return -1.

You may assume no duplicate exists in the array.

NOTE:- Array A was sorted in non-decreasing order before rotation.

1. NOTE : Think about the case when there are duplicates. Does your current solution work? How does the time complexity change?*</p>

<p><b>For Example :</b>
<br>

```python
Input 1:
    A = [4, 5, 6, 7, 0, 1, 2, 3]
    B = 4
Output 1:
    0
Explanation 1:
 Target 4 is found at index 0 in A.


Input 2:
    A = [5, 17, 100, 3]
    B = 6
Output 2:
    -1
```
</p>

<h2>Solution</h2>

***

```python
def circular_search(arr,n,ele):
    low = 0
    high = n-1
    while(low<=high):
        mid = (low+high)//2
        if arr[mid] == ele:
            return mid
        elif arr[mid]>=arr[low]:
            if arr[low]<=ele and ele<arr[mid]:
                high = mid-1
            else:
                low = mid + 1
        else:
            if ele>arr[mid] and ele<=arr[high]:
                low = mid + 1
            else:
                high = mid - 1
                
    return -1
class Solution:
    # @param A : tuple of integers
    # @param B : integer
    # @return an integer
    def search(self, A, B):
        return circular_search(A,len(A),B)
```