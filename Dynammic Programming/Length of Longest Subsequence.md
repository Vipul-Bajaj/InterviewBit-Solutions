<h1>Length of Longest Subsequence</h1>

<p>
Given an array of integers, A of length N, find the length of longest subsequence which is first increasing then decreasing.

<b>Input Format:</b>

    The first and the only argument contains an integer array, A.
<b>Output Format:</b>

    Return an integer representing the answer as described in the problem statement.
<b>Constraints:</b>

    1 <= N <= 3000
    1 <= A[i] <= 1e7
<b>Example:</b>

    Input 1:
        A = [1, 2, 1]

    Output 1:
        3

    Explanation 1:
        [1, 2, 1] is the longest subsequence.

    Input 2:
        [1, 11, 2, 10, 4, 5, 2, 1]

    Output 2:
        6
        
    Explanation 2:
        [1 2 10 4 2 1] is the longest subsequence.
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @return an integer
    def longestSubsequenceLength(self, A):
        n =len(A)
    
        if n == 0:
            return 0
        
        lis = [1]*n
        lds = [1]*n
        
        for i in range(1,n):
            for j in range(0,i):
                if A[j]<A[i]:
                    lis[i] = max(lis[i],lis[j]+1)
        
        for i in range(n-2,-1,-1):            
            for k in range(n-1,i,-1):
                if A[k]<A[i]:
                    lds[i] = max(lds[i],lds[k]+1)
                    
        ans = lis[0]+lds[0]-1
        for i in range(1,n):
            ans = max(lis[i]+lds[i]-1,ans)
        
        return ans
```