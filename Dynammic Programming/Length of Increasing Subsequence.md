<h1>Length of Increasing Subsequence</h1>

<p>
Find the longest increasing subsequence of a given array of integers, A.

In other words, find a subsequence of array in which the subsequence’s elements are in strictly increasing order, and in which the subsequence is as long as possible.
This subsequence is not necessarily contiguous, or unique.
In this case, we only care about the length of the longest increasing subsequence.

<b>Input Format:</b>

    The first and the only argument contains an integer array, A.
<b>Output Format:</b>

    Return an integer representing the length of the longest increasing subsequence.
<b>Constraints:</b>

    1 <= length(A) <= 2500
    1 <= A[i] <= 2000
<b>Example:</b>

    Input 1:
        A = [1, 2, 1, 5]

    Output 1:
        3
        
    Explanation 1:
        The sequence : [1, 2, 5]

    Input 2:
        A = [0, 8, 4, 12, 2, 10, 6, 14, 1, 9, 5, 13, 3, 11, 7, 15]
        
    Output 2:
        6

    Explanation 2:
        The sequence : [0, 2, 6, 9, 13, 15] or [0, 4, 6, 9, 11, 15] or [0, 4, 6, 9, 13, 15]
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @return an integer
    def lis(self, A):
        n =len(A)
    
        if n == 0:
            return 0
        
        dp = [1]*n
        
        for i in range(1,n):
            for j in range(0,i+1):
                if A[j]<A[i]:
                    dp[i] = max(dp[i],dp[j]+1)
                    
        return max(dp)
```