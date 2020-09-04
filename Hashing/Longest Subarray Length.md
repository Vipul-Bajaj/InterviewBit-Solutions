<h1>Longest Subarray Length</h1>

<p>
Given an integer array A of size N containing 0's and 1's only.
You need to find the length of the longest subarray having count of 1’s one more than count of 0’s.

Problem Constraints:

    1 <= N <= 10^5
Input Format:

    First and only argument is an integer array A of size N.
Output Format:
    Return an integer denoting the longest length of the subarray.
Example Input:

    Input 1:
        A = [0, 1, 1, 0, 0, 1]
    Input 2:
        A = [1, 0, 0, 1, 0]
    Output 1:
        5
    Output 2:
        1
    Explanation 1:
        Subarray of length 5, index 1 to 5 i.e 1, 1, 0, 0, 1. Count of 1 = 3, Count of 0 = 2.
    Explanation 2:
        Subarray of length 1 will be only subarray that follow the above condition.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def solve(self, A):
        n = len(A)
        max_length = 0
        s=0
        h = {}
        
        for i in range(n):
            if A[i]==0:
                s-=1
            else:
                s+=1
            if s==1:
                max_length = i+1
            if s not in h:
                h[s] = i
            if s-1 in h:
                max_length = max(max_length,i-h[s-1])
                
        return max_length
```
