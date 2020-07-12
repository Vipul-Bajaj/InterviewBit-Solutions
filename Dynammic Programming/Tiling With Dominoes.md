<h1>Tiling With Dominoes</h1>

<p>
Given an integer A you have to find the number of ways to fill a 3 x A board with 2 x 1 dominoes.

Return the answer modulo 109 + 7 .
Problem Constraints

    1 <= A <= 10^5
Input Format
    
    First and only argument is an integer A.
Output Format
    
    Return an integer denoting the number of ways to fill a 3 x A board with 2 x 1 dominoes with modulo 109 + 7.
Example Input

    Input 1:
        A = 2
    Input 2:
        A = 1
    Output 1:
        3
    Output 2:
        0
    Explanation 1:
        Following are all the 3 possible ways to fill up a 3 x 2 board.
        <img src="https://i.imgur.com/sXSWpJx.jpeg">
    Explanation 2:
        Not a even a single way exists to completely fill the grid of size 3 x 1

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return an integer
    def solve(self, A):
        n = A
        A = [0] * (n + 1) 
        B = [0] * (n + 1) 
        A[0] = 1
        A[1] = 0
        B[0] = 0
        B[1] = 1
        for i in range(2, n+1): 
            A[i] = A[i - 2] + 2 * B[i - 1] 
            B[i] = A[i - 1] + B[i - 2] 
          
        return A[n] % 1000000007
```