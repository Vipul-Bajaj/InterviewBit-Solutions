<h1>Array and Prime Divisors</h1>

<p>
You are given an array A having N positive distinct integers and an integer B.
You have to find the number of prime divisors of B present in A.

Input Format

    First argument given is an Array A, having N integers.
    Second argument given is an integer B. 
Output Format

    Return a single integer, i.e number of prime divisors of B present in A
Constraints

    1 <= N <= 1e4
    1 <= A[i] <= 1e5
    1 <= B <= 1e6
For Example

    Input:
        A = [1, 2, 3, 4, 5]
        B = 6
    Output:
        2
    Explanation:
        prime divisors of B in A are 2, 3
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return an integer
    def solve(self, A, B):
        
        primes = [True]*(B+1)
        primes[0],primes[1] = False,False
        
        for i in range(2,int(B**0.5)+1):
            if primes[i]:
                primes[i] = True
                j = i*2
                while j<=B:
                    primes[j] = False
                    j+=i
        
        count = 0
        
        for i in A:
            if i<B+1 and primes[i] and B%i==0:
                count+=1
                
        return count
```