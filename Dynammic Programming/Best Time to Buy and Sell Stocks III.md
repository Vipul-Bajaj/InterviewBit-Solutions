<h1>Best Time to Buy and Sell Stocks III</h1>

<p>
Say you have an array, A, for which the ith element is the price of a given stock on day i.
Design an algorithm to find the maximum profit. You may complete at most 2 transactions.

Return the maximum possible profit.

    Note: You may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).

Input Format:

    The first and the only argument is an array of integer, A.
Output Format:

    Return an integer, representing the maximum possible profit.
Constraints:

    1 <= len(A) <= 1e5
    1 <= A[i] <= 1e7
Example :

    Input 1:
        A = [1, 2, 1, 2]

    Output 1:
        2

    Explanation 1: 
        Day 0 : Buy 
        Day 1 : Sell
        Day 2 : Buy
        Day 3 : Sell

    Input 2:
        A = [7, 2, 4, 8, 7]

    Output 2:
        6

    Explanation 2:
        Day 1 : Buy
        Day 3 : Sell

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @return an integer
    def maxProfit(self, A):
        n = len(A)
        if n<1:
            return 0
        
        dp = [0 for i in range(n)]
        max_stock_value = A[n-1]
        
        for i in range(n-2,-1,-1):
            if A[i]>max_stock_value:
                max_stock_value = A[i]
                
            dp[i] = max(dp[i+1],max_stock_value-A[i])
            
        min_stock_value = A[0]
        
        for i in range(1,n):
            if A[i]<min_stock_value:
                min_stock_value = A[i]
                
            dp[i] = max(dp[i-1],dp[i]+A[i]-min_stock_value)
                
        return dp[n-1]
```