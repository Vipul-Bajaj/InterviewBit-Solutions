<h1>Coin Sum Infinite</h1>

<p>
You are given a set of coins S. In how many ways can you make sum N assuming you have infinite amount of each coin in the set.

Note : Coins in set S will be unique. Expected space complexity of this problem is O(N).

Examples:

    Input : 
        S = [1, 2, 3] 
        N = 4

    Return : 4

    Explanation : The 4 possible ways are
    {1, 1, 1, 1}
    {1, 1, 2}
    {2, 2}
    {1, 3}	

<b>Note that the answer can overflow. So, give us the answer % 1000007</b>
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return an integer
    def coinchange2(self, A, B):
        n = len(A)
    
        dp = [0] * (B+1)
        
        dp[0] = 1
        
        for i in range(0,n):
            for j in range(A[i],B+1):
                dp[j] += dp[j-A[i]]% 1000007
                
        return dp[B]% 1000007
```