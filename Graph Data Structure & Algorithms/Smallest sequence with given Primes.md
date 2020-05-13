<h1>Smallest sequence with given Primes</h1>

<p>
Given three prime number(p1, p2, p3) and an integer k. Find the first(smallest) k integers which have only p1, p2, p3 or a combination of them as their prime factors.

Example:

    Input :
    Prime numbers : [2,3,5]
    k : 5

    If primes are given as p1=2, p2=3 and p3=5 and k is given as 5, then the sequence of first 5 integers will be:

    Output:
    {2,3,4,5,6}

    Explanation :
    4 = p1 * p1 ( 2 * 2 )
    6 = p1 * p2 ( 2 * 3 )

Note: The sequence should be sorted in ascending order

<h2>Solution</h2>

***

```python
import heapq
class Solution:
    # @param A : integer
    # @param B : integer
    # @param C : integer
    # @param D : integer
    # @return a list of integers
    def solve(self, A, B, C, D):
        prime = [A,B,C]
        prime.sort()
        A,B,C = prime
        ugly = [0] * D
      
        iA = 0
        iB = 0
        iC = 0
      
        next_multiple_of_A = A
        next_multiple_of_B = B
        next_multiple_of_C = C
    
        for l in range(0, D): 
     
            ugly[l] = min(next_multiple_of_A, next_multiple_of_B, next_multiple_of_C) 
      
            if ugly[l] == next_multiple_of_A: 
                iA += 1
                next_multiple_of_A = ugly[iA-1] * A
      
            if ugly[l] == next_multiple_of_B: 
                iB += 1
                next_multiple_of_B = ugly[iB-1] * B
      
            if ugly[l] == next_multiple_of_C:  
                iC += 1
                next_multiple_of_C = ugly[iC-1] * C
      
        # return ugly[n] value 
        return sorted(ugly)
```