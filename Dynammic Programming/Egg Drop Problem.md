<h1>Egg Drop Problem</h1>

<p>
You are given A eggs, and you have access to a building with B floors from 1 to B.
Each egg is identical in function, and if an egg breaks, you cannot drop it again.

You know that there exists a floor C with 0 <= C <= B such that any egg dropped at a floor higher than C will break, and any egg dropped at or below floor C will not break.

Each move, you may take an egg (if you have an unbroken one) and drop it from any floor X (with 1 <= X <= B).

Your goal is to know with certainty what the value of C is.

What is the minimum number of moves that you need to know with certainty what C is, regardless of the initial value of C

Problem Constraints:

    1 <= A <= 100
    1 <= B <= 104
Input Format:

    First Argument is an integer A denoting number of eggs.
    Second Argument is an integer B denoting number of floors.
Output Format:

    Return an integer denoting the Minimum number of moves.
Example:

    Input 1:
        A = 1
        B = 2
    Input 2:
        A = 2
        B = 10
    Output 1:
        2
    Output 2:
        4 
    Explanation 1:
        Drop the egg from floor 1.  If it breaks, we know with certainty that F = 0.
        Otherwise, drop the egg from floor 2.If it breaks, we know with certainty that F=1.
        If it didn't break, then we know with certainty F = 2.
        Hence, we needed 2 moves in the worst case to know what F is with certainty.

<h2>Solution</h2>

***

```python
def binomialCoeff(x, n, k): 
  
    s = 0
    term = 1
    i = 1
    while(i <= n and s < k):  
        term *= x - i + 1
        term /= i
        s += term
        i += 1
    return s

class Solution:
    # @param A : integer
    # @param B : integer
    # @return an integer
    def solve(self, A, B):
        low = 1
        high = B

        while (low < high): 
      
            mid = (low + high) // 2
            if (binomialCoeff(mid, A, B) < B): 
                low = mid + 1
            else: 
                high = mid
      
        return int(low)
```