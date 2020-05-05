<h1>Ways To Color a 3xN Board</h1>

<p>
Given a 3 x A board, find the number of ways to color it using at most 4 colors such that no 2 adjacent boxes have same color.

Diagonal neighbors are not treated as adjacent boxes.

Return the ways modulo 109 + 7 as the answer grows quickly.
<b>Input Format:</b>

    The first and the only argument contains an integer, A.
<b>Output Format:</b>

    Return an integer representing the number of ways to color the board.
<b>Constraints:</b>

    1 <= A < 100000
<b>Example:</b>

    Input 1:
        A = 1

    Output 1:
        36

    Input 2:
        A = 2

    Output 2:
        588
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return an integer
    def solve(self, A):
        color3 = 24
        color2 = 12
        temp = 0
          
        for i in range(2, A + 1, 1): 
            temp = color3 
            color3 = (11 * color3 + 10 * color2 ) % 1000000007
                  
            color2 = ( 5 * temp + 7 * color2 ) % 1000000007
          
        num = (color3 + color2) % 1000000007
                              
        return num 
```