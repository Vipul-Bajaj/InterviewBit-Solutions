<h1>Search in Bitonic Array</h1>

<p>
Given a bitonic sequence A of N distinct elements, write a program to find a given element B in the bitonic sequence in O(logN) time.

NOTE:

    A Bitonic Sequence is a sequence of numbers which is first strictly increasing then after a point strictly decreasing.


Problem Constraints

    3 <= N <= 105
    1 <= A[i], B <= 108
    Given array always contain a bitonic point.
    Array A always contain distinct elements.

Input Format

    First argument is an integer array A denoting the bitonic sequence.
    Second argument is an integer B.
Output Format
    
    Return a single integer denoting the position (0 index based) of the element B in the array A if B doesn't exist in A return -1.
Example:

    Input 1:
        A = [3, 9, 10, 20, 17, 5, 1]
        B = 20
    Input 2:
        A = [5, 6, 7, 8, 9, 10, 3, 2, 1]
        B = 30
    Output 1:
        3
    Output 2:
        -1
    Explanation 1:
        B = 20 present in A at index 3
    Explanation 2:
        B = 30 is not present in A

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return an integer
    def solve(self, A, B):
        low,high = 0,len(A)-1
        mid_point = None
        while low<=high:
            mid = (low+high)//2
            if A[mid]>A[mid-1] and A[mid]>A[mid+1]:
                mid_point = mid
                break
            elif A[mid]>A[mid-1] and A[mid]<A[mid+1]:
                low = mid
            elif A[mid]<A[mid-1] and A[mid]>A[mid+1]:
                high = mid
            
        if A[mid_point] == B:
            return mid_point
            
        low = 0
        high = mid_point-1
        while low<=high:
            mid = (low+high)//2
            if A[mid]==B:
                return mid
            elif B<A[mid]:
                high = mid-1
            else:
                low = mid+1
                
        low = len(A)-1
        high = mid_point+1
        while low>=high:
            mid = (low+high)//2
            if A[mid]==B:
                return mid
            elif B<A[mid]:
                high = mid+1
            else:
                low = mid-1
                
        return -1
```