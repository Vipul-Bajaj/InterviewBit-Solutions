<h1>Simple Queries</h1>

<p>You are given an array A having N integers.

You have to perform the following steps in a given order.

generate all subarrays of A.
take the maximum element from each subarray of A and insert it into a new array G.
replace every element of G with the product of their divisors mod 1e9 + 7.
sort G in descending order
perform Q queries
In each query, you are given an integer K, where you have to find the Kth element in G.

    Note: Your solution will run on multiple test cases so do clear global variables after using them.


Input Format

    The first argument given is an Array A, having N integers.
    The second argument given is an Array B, where B[i] is the ith query.
Output Format

    Return an Array X, where X[i] will have the answer for the ith query.
Constraints

    1 <= N <= 1e5
    1 <= A[i] <= 1e5
    1 <= Q <= 1e5
    1 <= k <= (N * (N + 1))/2 
For Example

    Input:
        A = [1, 2, 4]
        B = [1, 2, 3, 4, 5, 6]
    Output:
        X = [8, 8, 8, 2, 2, 1]
    
    Explanation:
        subarrays of A	  maximum element
        ------------------------------------
        1. [1]							1
        2. [1, 2]						2
        3. [1, 2, 4]					4
        4. [2]							2
        5. [2, 4]						4
        6. [4]							4

        original
        G = [1, 2, 4, 2, 4, 4]
        
        after changing every element of G with product of their divisors
        G = [1, 2, 8, 2, 8, 8]
        
        after sorting G in descending order
        G = [8, 8, 8, 2, 2, 1]
</p>

<h2>Solution</h2>

***

```python
def prod_of_divisors(n):
    prod = 1
    i = 1
    while i <= (n**0.5): 
          
        if (n % i == 0) : 
            if (n // i == i) : 
                prod*=i
            else : 
                prod*=i*n//i
        i = i + 1
    return prod%1000000007
    
class Solution:
    # @param A : list of integers
    # @param B : list of integers
    # @return a list of integers
    def solve(self, A, B):
        n = len(A)
        G = []
        for i in range(n):
            _max = max(A[i:])
            prod = prod_of_divisors(_max)
            G += [prod]*(n-i)
            
        G.sort(reverse=True)
        
        res = [0]*len(B)
        for i in range(len(B)):
            res[i] = G[B[i]-1]
            
        return res
```