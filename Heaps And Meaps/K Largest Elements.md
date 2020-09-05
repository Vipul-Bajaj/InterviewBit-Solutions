<h1>K Largest Elements</h1>

<p>
Given an 1D integer array A of size N you have to find and return the B largest elements of the array A.

NOTE:

1. Return the largest B elements in any order you like.

Problem Constraints:

    1 <= N <= 10^5
    1 <= B <= N
    1 <= A[i] <= 10^3

Input Format:

    First argument is an 1D integer array A
    Second argument is an integer B.
Output Format:
    Return a 1D array of size B denoting the B largest elements.
Example Input:

    Input 1:
        A = [11, 3, 4]
        B = 2
    Input 2:
        A = [11, 3, 4, 6]
        B = 3
    Output 1:
        [11, 4]
    Output 2:
        [4, 6, 11]
    Explanation 1:
        The two largest elements of A are 11 and 4
    Explanation 2:
        The three largest elements of A are 11, 4 and 6
</p>

<h2>Solution</h2>

***

```python
import heapq
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return a list of integers
    def solve(self, A, B):
        heapq.heapify(A)
        return heapq.nlargest(B,A)
```
