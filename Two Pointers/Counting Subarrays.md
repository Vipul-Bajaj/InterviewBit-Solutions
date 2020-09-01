<h1>Counting Subarrays</h1>

<p>
Given an array A of N non-negative numbers and you are also given non-negative number B.

You need to find the number of subarrays in A having sum less than B. We may assume that there is no overflow.

Problem Constraints:

    1 <= N <= 10^4
    1 <= A[i] <= 100
    1 <= B <= 10^8
Input Format:

    First argument is an integer array A of size N.
    Second argument is an integer B.
    
Output Format:

    Return an integer denoting the number of subarrays in A having sum less than B.
    
Example Input:

    Input 1:
        A = [2, 5, 6]
        B = 10
    Input 2:
        A = [1, 11, 2, 3, 15]
        B = 10
    Output 1:
        4
    Output 2:
        4
    Explanation 1:
        The subarrays with sum less than B are {2}, {5}, {6} and {2, 5},
    Explanation 2:
        The subarrays with sum less than B are {1}, {2}, {3} and {2, 3}
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return an integer
    def solve(self, A, B):
        n = len(A)
        c=0
        for i in range(n):
            s = 0
            for j in range(i,n):
                s+=A[j]
                if s<B:
                    c+=1
                else:
                    break
                
        return c
```
