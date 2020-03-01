<h1>Prime Sum</h1>

<p>
Given an even number ( greater than 2 ), return two prime numbers whose sum will be equal to given number.

NOTE A solution will always exist. read Goldbach’s conjecture
</p>

<p>
<b>Example :</b>
<br>

    Input : 4
    Output: 2 + 2 = 4

If there are more than one solutions possible, return the lexicographically smaller solution.
    
    If [a, b] is one solution with a <= b,
    and [c,d] is another solution with c <= d, then

    [a, b] < [c, d] 

    If a < c OR a==c AND b < d. 
</p>

<h2>Solution</h2>

***

```python
def SieveOfEratosthenes(n): 
    prime = [True for i in range(n+1)] 
    p = 2
    while (p * p <= n): 
        if (prime[p] == True): 
            for i in range(p * p, n+1, p): 
                prime[i] = False
        p += 1
    
    primes = []
    for p in range(2, n): 
        if prime[p]: 
            primes.append(p)
            
    return primes
    
class Solution:
    # @param A : integer
    # @return a list of integers
    def primesum(self, A):
        primes = SieveOfEratosthenes(A)
        
        i,j=0,len(primes)-1
        
        while i<=j:
            if primes[i]+primes[j]==A:
                return [primes[i],primes[j]]
            elif primes[i]+primes[j]<A:
                i+=1
            else:
                j-=1
                
        return None
            
```