<h1>MinimiZe</h1>

<p>
You are given two positive integers A and B. An equation is given, Z = P*A + Q*B.
Where P and Q can be any integers, while A and B are the given integers.
If you replace P and Q with appropriate values, find the minimum positive value that Z can achieve through the equation.

    Note: Your solution will run on multiple test cases so do clear global variables after using them.

Input:

    A: Integer
    B: Integer
Output:

    Minimum positive value of Z
Constraints:

    1 <= A, B <= 10^9
    Z has to be the minimum positive value
    P, Q can be any integers (positive, negative, or zero)
Example:

    Input
        A: 2
        B: 3
    Output
        1
    Explanation
        Z = P*A + Q*B,
        Z = P*2 + Q*3,
        Let P = 2, and Q = -1, we get
        Z = 2*2 + -1*3
        Z = 4 - 3
        Z = 1

    Hence minimum positive value of Z is 1.
</p>

<h2>Solution</h2>

***

```python
def gcd(a, b):  
    if a == 0 : 
        return b       
    return gcd(b % a, a)
class Solution:
    # @param A : integer
    # @param B : integer
    # @return an integer
    def solve(self, A, B):
        return gcd(A,B)
```