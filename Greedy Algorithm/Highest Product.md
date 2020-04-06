<h1>Highest Product</h1>

<p>
Given an array A, of N integers A.Return the highest product possible by multiplying 3 numbers from the array.

    NOTE: Solution will fit in a 32-bit signed integer.

Input Format:
    
    The first and the only argument is an integer array A.

Output Format:

    Return the highest possible product.

Constraints:

    1 <= N <= 5e5

Example:

    Input 1:
        A = [1, 2, 3, 4]
    Output 1:
        24
    Explanation 1:
        2 * 3 * 4 = 24

    Input 2:
        A = [0, -1, 3, 100, 70, 50]
    Output 2:
        350000
    Explanation 2:
        70 * 50 * 100 = 350000

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def maxp3(self, A):
        if len(A)<3:
            return None
        A.sort()
        if A[0]>=0 or len(A)==3:
            return A[-1]*A[-2]*A[-3]
        np = A[-1]*A[-2]*A[-3]
        p = 0
        if A[0]<0 and A[1]<0:
            p = abs(A[0])*abs(A[1])*A[-1]
        return max(np,p)
```