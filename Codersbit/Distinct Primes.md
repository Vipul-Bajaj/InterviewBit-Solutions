<h1>Distinct Primes</h1>

<p>
You have given an array A having N integers. Let say G is the product of all elements of A.
You have to find the number of distinct prime divisors of G.

Input Format

    The first argument given is an Array A, having N integers.
Output Format

    Return an Integer, i.e number of distinct prime divisors of G.
Constraints

    1 <= N <= 1e5
    1 <= A[i] <= 1e5
For Example

    Input:
        A = [1, 2, 3, 4]
    Output:
        2
    Explanation:
        here G = 1 * 2 * 3 * 4 = 24
        and distinct prime divisors of G are [2, 3]
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def solve(self, A):
        m = set()
  
        for i in range (len(A)) : 
            sq = int(A[i]**0.5) 
            for j in range(2, sq + 1) : 
                if (A[i] % j == 0) : 
                    m.add(j) 
                    while (A[i] % j == 0) : 
                        A[i] //= j 
            if (A[i] > 2) : 
                m.add(A[i]) 
      
        return len(m)
```