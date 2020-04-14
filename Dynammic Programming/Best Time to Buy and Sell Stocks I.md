<h1>Best Time to Buy and Sell Stocks I</h1>

<p>
If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

Return the maximum possible profit.

Input Format:

    The first and the only argument is an array of integers, A.
Output Format:

    Return an integer, representing the maximum possible profit.
Constraints:

    0 <= len(A) <= 7e5
    1 <= A[i] <= 1e7
Examples:

    Input 1:
        A = [1,2]

    Output 1:
        1
        
    Explanation 1:
        Buy the stock on day 0, and sell it on day 1.

    Input 2:
        A = [1, 4, 5, 2, 4]

    Output 2:
        4

    Explanation 2:
        Buy the stock on day 0, and sell it on day 2.

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
        max_profit = 0
        min_stock_value = A[0]
        
        for i in range(1,n):
            if A[i]<min_stock_value:
                min_stock_value = A[i]
            if A[i]-min_stock_value>max_profit:
                max_profit = A[i]-min_stock_value
                
        return max_profit
```