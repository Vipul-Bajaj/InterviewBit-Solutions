<h1>0-1 Knapsack</h1>

<p>
Given two integer arrays A and B of size N each which represent values and weights associated with N items respectively.Also given an integer C which represents knapsack capacity.

Find out the maximum value subset of A such that sum of the weights of this subset is smaller than or equal to C.

NOTE:

    You cannot break an item, either pick the complete item, or don’t pick it (0-1 property).

Problem Constraints:

    1 <= N <= 10^3
    1 <= C <= 10^3
    1 <= A[i], B[i] <= 10^3
Input Format:

    First argument is an integer array A of size N denoting the values on N items.
    Second argument is an integer array B of size N denoting the weights on N items.=
    Third argument is an integer C denoting the knapsack capacity.
Output Format:

    Return a single integer denoting the maximum value subset of A such that sum of the weights of this subset is smaller than or equal to C.
Example:

    Input 1:
        A = [60, 100, 120]
        B = [10, 20, 30]
        C = 50
    Input 2:
        A = [10, 20, 30, 40]
        B = [12, 13, 15, 19]
        C = 10
    Output 1:
        220
    Output 2:
        0
    Explanation 1:
        Taking items with weight 20 and 30 will give us the maximum value i.e 100 + 120 = 220
    Explanation 2:
        Knapsack capacity is 10 but each item has weight greater than 10 so no items can be considered in the knapsack therefore answer is 0.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : list of integers
    # @param C : integer
    # @return an integer
    def solve(self, A, B, C):
        dp = [[0 for j in range(C+1) ]for i in range(len(A)+1)]
        n = len(A)
        for i in range(n + 1): 
            for w in range(C + 1): 
                if i == 0 or w == 0: 
                    dp[i][w] = 0
                elif B[i-1] <= w: 
                    dp[i][w] = max(A[i-1] + dp[i-1][w-B[i-1]],  dp[i-1][w]) 
                else: 
                    dp[i][w] = dp[i-1][w] 
      
        return dp[n][C] 
```