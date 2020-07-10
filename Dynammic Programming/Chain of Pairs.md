<h1>Chain of Pairs</h1>

<p>
Given a N * 2 array A where (A[i][0], A[i][1]) represents the ith pair.
In every pair, the first number is always smaller than the second number.

A pair (c, d) can follow another pair (a, b) if b < c , similarly in this way a chain of pairs can be formed.

Find the length of the longest chain subsequence which can be formed from a given set of pairs.
Problem Constraints

    1 <= N <= 103
    1 <= A[i][0] < A[i][1] <= 104
Input Format
    
    First and only argument is an 2D integer array A of size N * 2 representing the N pairs.
Output Format
    
    Return a single integer denoting the length of longest chain subsequence of pairs possible under given constraint.
Example Input

    Input 1:
        A = [  [5, 24]
                [39, 60]
                [15, 28]
                [27, 40]
                [50, 90]
            ]
    Input 2:
        A = [   [10, 20]
                [1, 2]
            ]
    Output 1:
        3
    Output 2:
        1
    Explanation 1:
        Longest chain that can be formed is of length 3, and the chain is [ [5, 24], [27, 40], [50, 90] ]
    Explanation 2:
        Longest chain that can be formed is of length 1, and the chain is [ [1, 2] ] or [ [10, 20] ]

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @return an integer
    def solve(self, A):
        n = len(A)
    
        # A.sort()
        
        max_length = 0
      
        mcl = [1 for i in range(n)] 
      
        for i in range(1, n): 
            for j in range(0, i): 
                if (A[i][0] > A[j][1] and mcl[i] < mcl[j] + 1): 
                    mcl[i] = mcl[j] + 1
      
        for i in range(n): 
            if (max_length < mcl[i]): 
                max_length = mcl[i] 
      
        return max_length
```