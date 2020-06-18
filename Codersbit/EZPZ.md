<h1>EZPZ</h1>

<p>
Given a number N, find the minimum number of prime numbers required, whose summation gives you N.

Eg: N = 4

4 can be denoted as 2 + 2, hence minimum number of primes needed is 2.
If not possible, return -1.

    Note that 1 is not a prime number.

Input:

    N: Integer
Output:

    Integer
Constraints:

    0 <= N <= 10^9
Example:

    Input
        N: 9
    Output
        2
    Explanation
        9 = 2 + 7
    Input
        N: 11
    Output
        1
    Explanation
        11 itself is a prime.
</p>

<h2>Solution</h2>

***

```python
def isPrime(A):
    for i in range(2,int(A**0.5)+1):
        if A%i == 0:
            return False
    return True
class Solution:
    # @param A : integer
    # @return an integer
    def solve(self, A):
        if A==1 or A == 0:
            return -1
        if isPrime(A):
            return 1
        if A%2 == 0:
            return 2
        if isPrime(A-2):
            return 2
        return 3
```