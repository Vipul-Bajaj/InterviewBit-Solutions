<h1>Prime Subarrays</h1>

<p>
You are given an integer array A of size N.

You have to find the number of subarrays those have Prime Sum.

Input Format

    The first argument given is an Array A, having N integers.
Output Format

    Return an Integer, i.e number of subarrays those have prime sum.
Constraints

    1 <= N <= 1e3
    1 <= A[i] <= 1e3
For Example

    Input:
        A = [1, 2, 3]
    Output:
        4
    Explanation:
        no. subarray      sum
        1.  [1]			  1
        2.  [1, 2]		  3
        3.  [1, 2, 3]     6
        4.  [2]		      2
        5.  [2, 3]		  5
        6.  [3]		      3

        here we have 4 subarrays(2, 4, 5, 6) those have prime sum. 
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def solve(self, A):
        B = sum(A)
        primes = [True]*(B+1)
        primes[0],primes[1] = False,False
        
        for i in range(2,B+1):
            if primes[i]:
                primes[i] = True
                j = i*2
                while j<=B:
                    primes[j] = False
                    j+=i
                    
        count = 0
        n = len(A)
        for i in range(n):
            for j in range(i,n):
                s = sum(A[i:j+1])
                if primes[s]:
                    count+=1
                    
        return count
```