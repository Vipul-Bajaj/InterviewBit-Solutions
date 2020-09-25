<h1>Best Time to Buy and Sell Stock atmost B times</h1>

<p>
Given an array of integers A of size N in which ith element is the price of the stock on day i.
You can complete atmost B transactions.
Find the maximum profit you can achieve.
NOTE: You may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again)

Problem Constraints

    1 <= N <= 500
    0 <= A[i] <= 10^6
    0 <= B <= 10^9
Input Format

    The First argument given is the integer array A.
    The Second argument is integer B.
Output Format
    
    Return the maximum profit you can achieve by doing atmost B transactions.
Example:

    Input 1:
        A = [2, 4, 1]
        B = 2
    Input 2:
        A = [3, 2, 6, 5, 0, 3]
        B = 2
    Output 1:
        2
    Output 2:
        7
    Explanation 1:
        Buy on day 1 (price = 2) and sell on day 2 (price = 4), 
        Profit = 4 - 2 = 2
    Explanation 2:
        Buy on day 2 (price = 2) and sell on day 3 (price = 6), profit = 6 - 2 = 4.
        Then buy on day 5 (price = 0) and sell on day 6 (price = 3), profit = 3 - 0 = 3.
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return an integer
    def solve(self, A, B):
        n = len(A)
        if B > n:
            B = n
        dp = [0]*n
    
        for k in range(1, B+1): 
            prevtrans = -A[0]
            newdp = [0]*n
            for i in range(1,n):
                newdp[i] = max(newdp[i-1],A[i]+prevtrans)
                prevtrans = max(prevtrans,-A[i]+dp[i])
                
            dp = newdp
            
        return dp[n-1]
```
