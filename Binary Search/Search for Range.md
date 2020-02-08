<h1>Search for Range</h1>

<p>
Given a sorted array of integers A(0 based index) of size N, find the starting and ending position of a given integar B in array A.

Your algorithm’s runtime complexity must be in the order of O(log n).

Return an array of size 2, such that first element = starting position of B in A and second element = ending position of B in A, if B is not found in A return [-1, -1].
</p>

<p><b>Example :</b>
<br>

```python
Input 1:
    A = [5, 7, 7, 8, 8, 10]
    B = 8
Output 1:
    [3, 4]
Explanation 1:
    First occurence of 8 in A is at index 3
    Second occurence of 8 in A is at index 4
    ans = [3, 4]

Input 2:
    A = [5, 17, 100, 111]
    B = 3
Output 2:
    [-1, -1]
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @param B : integer
    # @return a list of integers
    def searchRange(self, A, B):
        n = len(A)
    
        l,h = 0,n-1
        s,e = -1,-1
        
        while l<=h:
            mid = (l+h)//2
            
            if (mid==l and A[mid] == B) or (A[mid]==B and A[mid-1]<B):
                s = mid
                break
            elif A[mid]<B:
                l = mid+1
            else:
                h = mid-1
        
        l,h = 0,n-1        
        while l<=h:
            mid = (l+h)//2
            
            if (mid==h and A[mid] == B) or (A[mid]==B and A[mid+1]>B):
                e = mid
                break
            elif A[mid]<=B:
                l = mid+1
            else:
                h = mid-1
                
        return [s,e]
```