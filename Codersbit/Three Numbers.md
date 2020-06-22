<h1>Three Numbers</h1>

<p>
Given three positive numbers A, B, and C.
Find the number of positive integers less than D that are divisible by either of A, B or C.

Input Format

    The 1st argument given is an Integer A.
    The 2nd argument given is an Integer B.
    The 3rd argument given is an Integer C.
    The 4th argument given is an Integer D.
Output Format

    Return an Integer X, the number of positive integers that are divisible by either of A, B, or C.
Constraints

    1 <= A, B, C, D <= 1e9
For Example

    Input:
        A = 2
        B = 3
        C = 4
        D = 10
    Output:
        6
    Explanation:
        positive numbers less than D that are divisible by either of A, B or C are
        2, 3, 4, 6, 8, 9
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @param B : integer
    # @param C : integer
    # @param D : integer
    # @return an integer
    def solve(self, A, B, C, D):
        def gcd(a,b): 
            if a == 0: 
                return b 
            return gcd(b % a, a) 
    
        def lcm(a,b): 
            return (a*b) / gcd(a,b) 
        
        if A==1 or B==1 or C==1:
            ans=D-1
        else:
            x=lcm(A,B)
            y=lcm(A,C)
            z=lcm(B,C)
            d=D-1
            ans=d//A + d//B +d//C - d//x - d//y - d//z
        return int(ans)
```