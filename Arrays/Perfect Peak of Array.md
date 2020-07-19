<h1>Perfect Peak of Array</h1>

<p>
Given an integer array A of size N.

You need to check that whether there exist a element which is strictly greater than all the elements on left of it and strictly smaller than all the elements on right of it.

If it exists return 1 else return 0.

NOTE:

    Do not consider the corner elements i.e A[0] and A[N-1] as the answer.

Problem Constraints

    3 <= N <= 10^5
    1 <= A[i] <= 10^9
Input Format

    First and only argument is an integer array A containing N integers.
Output Format
    
    Return 1 if there exist a element that is strictly greater than all the elements on left of it and strictly smaller than all the elements on right of it else return 0.
Example:

    Input 1:
        A = [5, 1, 4, 3, 6, 8, 10, 7, 9]
    Input 2:
        A = [5, 1, 4, 4]
    Output 1:
        1
    Output 2:
        0
    Explanation 1:
        A[4] = 6 is the element we are looking for.
        All elements on left of A[4] are smaller than it and all elements on right are greater.
    Explanation 2:
        No such element exits.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def perfectPeak(self, A):
        n = len(A)
    
        left_max = [-2**31]*n
        
        for i in range(1,n):
            left_max[i] = max(left_max[i-1],A[i-1])
        
        right_min = A[-1]
        
        for i in range(n-2,0,-1):
            if A[i]<right_min and A[i]>left_max[i]:
                return 1
            right_min = min(right_min,A[i])
        
        return 0
```