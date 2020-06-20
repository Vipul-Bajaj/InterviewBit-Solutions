<h1>The Sequence Game</h1>

<p>
Scooby is a great mathematician and loves playing with sequences. He has a sequence whose ith term is given as follows:
Ti = ik - (i-1)k
where k is an integer. You have to find the sum of first N terms of the series. In order words you need to find the value of the following expression :
T1+T2+…TN. As this value can be really large, output the value modulo 10^9+7.

Constraints:

    Number of testcases T: 1<=T<=1000
    1<=N<=1000000000
    1<=K<=1000000000
Input:

    An integer N
    An integer K
Note:

    Your code will run against multiple testcases.
Output:

    One integer corresponding to the value of the above mentioned expression modulo 1000000007. 
Examples:

    Input:
        3
        2 
    Output:
        9
    Explanation:
        The three terms of the sequence are :
        T1=1
        T2=3
        T3=5

        Threfore the value of T1+T2+T3 is 9 and hence the answer is 9.
</p>

<h2>Solution</h2>

***

```python
def power(x, y, p) : 
    res = 1     # Initialize result 
  
    # Update x if it is more 
    # than or equal to p 
    x = x % p  
      
    if (x == 0) : 
        return 0
  
    while (y > 0) : 
          
        # If y is odd, multiply 
        # x with result 
        if ((y & 1) == 1) : 
            res = (res * x) % p 
  
        # y must be even now 
        y = y >> 1      # y = y/2 
        x = (x * x) % p 
          
    return res 
class Solution:
    # @param A : integer
    # @param B : integer
    # @return an integer
    def solve(self, A, B):

        return power(A,B,1000000007)
```