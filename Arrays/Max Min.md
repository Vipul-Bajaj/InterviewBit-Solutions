<h1>Max Min</h1>

<p>
Given an array A of size N. You need to find the sum of Maximum and Minimum element in the given array.

NOTE: You should make minimum number of comparisons.

Problem Constraints

    1 <= N <= 10^5
    -10^9 <= A[i] <= 10^9
Input Format

    First and only argument is an integer array A of size N.
Output Format
    
    Return an integer denoting the sum Maximum and Minimum element in the given array.
Example:

    Input 1:
        A = [-2, 1, -4, 5, 3]
    Input 2:
        A = [1, 3, 4, 1]
    Output 1:
        1
    Output 2:
        5
    Explanation 1:
        Maximum Element is 5 and Minimum element is -4. (5 + (-4)) = 1. 
    Explanation 2:
        Maximum Element is 4 and Minimum element is 1. (4 + 1) = 5.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def solve(self, A):
        n = len(A)
    
        _min = A[0]
        _max = A[0]
        
        for i in range(1,n):
            if A[i]>_max:
                _max = A[i]
            if A[i]<_min:
                _min = A[i]
    
        return _min+_max
```