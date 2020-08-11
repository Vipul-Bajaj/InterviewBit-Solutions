<h1>Minimum Difference Subsets!</h1>

<p>
Given an integer array A containing N integers.
You need to divide the array A into two subsets S1 and S2 such that the absolute difference between their sums is minimum.

Find and return this minimum possible absolute difference.

NOTE:
1. Subsets can contain elements from A in any order (not necessary to be contiguous).
2. Each element of A should belong to any one subset S1 or S2, not both.
3. It may be possible that one subset remains empty.

Problem Constraints:

    1 <= N <= 100
    1 <= A[i] <= 100
Input Format:

    First and only argument is an integer array A.
Output Format:

    Return an integer denoting the minimum possible difference among the sums of two subsets.
Example:

    Input 1:
        A = [1, 6, 11, 5]
    Output 1:
        1
    Explanation 1:
        Subset1 = {1, 5, 6}, sum of Subset1 = 12
        Subset2 = {11}, sum of Subset2 = 11

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def solve(self, A):
        n = len(A)
        s = sum(A)
        dp = [[0 for j in range(s+1) ]for i in range(n+1)]
        
        for i in range(n+1):
            dp[i][0] = 1
            
        for i in range(1,n+1):
            for j in range(1,s+1):
                dp[i][j] = dp[i-1][j]
                
                if A[i-1]<=j:
                    dp[i][j] = dp[i][j] or dp[i-1][j-A[i-1]]
        
        diff = 2**31            
        for j in range(s // 2, -1, -1): 
            if dp[n][j] == True: 
                diff = s - (2 * j) 
                break
                  
        return diff 
```