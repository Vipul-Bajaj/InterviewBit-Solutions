<h1>Sort array with squares</h1>

<p>
Given a sorted array A containing N integers both positive and negative.

You need to create another array containing the squares of all the elements in A and return it in non-decreasing order.

Try to this in O(N) time.

Problem Constraints

    1 <= N <= 10^5.
    -10^3 <= A[i] <= 103
Input Format

    First and only argument is an integer array A.
Output Format
    
    Return a integer array as described in the problem above.
Example:

    Input 1:
        A = [-6,- 3, -1, 2, 4, 5]
    Input 2:
        A = [-5, -4, -2, 0, 1]
    Output 1:
        [1, 4, 9, 16, 25, 36]
    Output 2:
        [0, 1, 4, 16, 25]

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return a list of integers
    def solve(self, A):
        n = len(A)
        new_arr = [-1]*n
        mid = 0
        for i in range(n):
            if A[i]>=0:
                mid = i
                break
        i = mid-1
        j = mid
        k = 0
        while i>=0 and j<n:
            sq_i = A[i]*A[i]
            sq_j = A[j]*A[j]
            
            if sq_i<=sq_j:
                new_arr[k] = sq_i
                i-=1
            else:
                new_arr[k] = sq_j
                j+=1
            k+=1
        while i>=0:
            new_arr[k] = A[i]*A[i]
            i-=1
            k+=1
        while j<n:
            new_arr[k] = A[j]*A[j]
            j+=1
            k+=1
        return new_arr
```