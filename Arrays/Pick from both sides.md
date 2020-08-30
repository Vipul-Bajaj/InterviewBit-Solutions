<h1>Pick from both sides</h1>

<p>
Given an integer array A of size N.

You can pick B elements from either left or right end of the array A to get maximum sum.

Find and return this maximum possible sum.

NOTE: Suppose B = 4 and array A contains 10 elements then:

1. You can pick first four elements or can pick last four elements or can pick 1 from front and 3 from back etc . you need to return the maximum possible sum of elements you can pick.

Problem Constraints

    1 <= N <= 10^5
    1 <= B <= N
    -1^3 <= A[i] <= 10^3
Input Format

    First argument is an integer array A.
    Second argument is an integer B.

Output Format
    
    Return an integer denoting the maximum possible sum of elements you picked.
Example:

    Input 1:
        A = [5, -2, 3 , 1, 2]
        B = 3
    Input 2:
        A = [1, 2]
        B = 1
    Output 1:
        8
    Output 2:
        2
    Explanation 1:
        Pick element 5 from front and element (1, 2) from back so we get 5 + 1 + 2 = 8
    Explanation 2:
        Pick element 2 from end as this is the maximum we can get

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return an integer
    def solve(self, A, B):
        n = len(A)
        max_sum = 0
        for i in range(B):
            max_sum += A[i]
        
        sum_last = max_sum
        ind = n-1
        ans = max_sum
        for i in range(B-1,-1,-1):
            sum_last-=A[i]
            max_sum = sum_last
            max_sum+=A[ind]
            ind-=1
            ans = max(ans,max_sum)
            sum_last = max_sum
            
        return ans
```