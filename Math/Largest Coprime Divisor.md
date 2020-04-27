<h1>Largest Coprime Divisor</h1>

<p>
You are given two positive numbers A and B. You need to find the maximum valued integer X such that:

1. X divides A i.e. A % X = 0
2. X and B are co-prime i.e. gcd(X, B) = 1

For example,

    A = 30
    B = 12
    We return
    X = 5
</p>

<h2>Solution</h2>

***

```python
def gcd(a,b): 

    while b>0:
        old_a = a
        a=b
        b=old_a%b
        
    return a
    
class Solution:
    # @param A : integer
    # @param B : integer
    # @return an integer
    def cpFact(self, A, B):
        if gcd(A,B)==1:
            return A
        
        g = gcd(A,B)
        while g!=1:
            A = A//g
            g = gcd(A,B)
            
        return A
```