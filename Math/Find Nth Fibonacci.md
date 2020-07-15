<h1>Find Nth Fibonacci</h1>

<p>
Given an integer A you need to find the Ath fibonacci number modulo 109 + 7.
The first fibonacci number F1 = 1
The first fibonacci number F2 = 1
The nth fibonacci number Fn = Fn-1 + Fn-2 (n > 2)
Problem Constraints

    1 <= A <= 10^9.
Input Format

    First argument is an integer A.
Output Format
    
    Return a single integer denoting Ath fibonacci number modulo 10^9 + 7
Example:

    Input 1:
        A = 4
    Input 2:
        A = 3
    Output 1:
        3
    Output 2:
        2
    Explanation 1:
        F3 = F2 + F1 = 1 + 1 = 2
        F4 = F3 + F2 = 2 + 1 = 3
    Explanation 2:
        F3 = F2 + F1 = 1 + 1 = 2

<h2>Solution</h2>

***

```python
def fib(n): 
      
    F = [[1, 1], 
         [1, 0]] 
    if (n == 0): 
        return 0
    power(F, n - 1) 
          
    return F[0][0] 
      
def multiply(f, m): 
    mod=1000000007
    
    a=(((f[0][0]*m[0][0])%mod)+((f[0][1]*m[1][0])%mod))%mod
    b=(((f[0][0]*m[0][1])%mod)+((f[0][1]*m[1][1])%mod))%mod
    c=(((f[1][0]*m[0][0])%mod)+((f[1][1]*m[1][0])%mod))%mod
    d=(((f[1][0]*m[0][1])%mod)+((f[1][1]*m[1][1])%mod))%mod
    f[0][0]=a
    f[0][1]=b
    f[1][0]=c
    f[1][1]=d
          
def power(F, n): 
  
    if( n == 0 or n == 1): 
        return; 
    M = [[1, 1], 
         [1, 0]]; 
          
    power(F, n // 2) 
    multiply(F, F) 
          
    if (n % 2 != 0): 
        multiply(F, M) 
class Solution:
    # @param A : integer
    # @return an integer
    def solve(self, A):
        return fib(A)
```