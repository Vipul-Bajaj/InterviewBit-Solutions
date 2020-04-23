<h1>Longest Arithmetic Progression</h1>

<p>
Find longest Arithmetic Progression in an integer array A of size N, and return its length.

More formally, find longest sequence of indices, 0 < i1 < i2 < … < ik < ArraySize(0-indexed) such that sequence A[i1], A[i2], …, A[ik] is an Arithmetic Progression.

Arithmetic Progression is a sequence in which all the differences between consecutive pairs are the same, i.e sequence B[0], B[1], B[2], …, B[m - 1] of length m is an Arithmetic Progression if and only if B[1] - B[0] == B[2] - B[1] == B[3] - B[2] == … == B[m - 1] - B[m - 2]

Note: The common difference can be positive, negative or 0.

<b>Input Format :</b>

    The first and the only argument of input contains an integer array, A.
<b>Output Format :</b>

    Return an integer, representing the length of the longest possible arithmetic progression.
<b>Constraints :</b>

    1 <= N <= 1000
    1 <= A[i] <= 1e9
<b>Examples :</b>

    Input 1:
        A = [3, 6, 9, 12]

    Output 1:
        4

    Explanation 1:
        [3, 6, 9, 12] form an arithmetic progression.

    Input 2:
        A = [9, 4, 7, 2, 10]

    Output 2:
        3

    Explanation 2:
        [4, 7, 10] form an arithmetic progression.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @return an integer
    def solve(self, A):
        dp = {}
        for i in range(len(A)):
            for j in range(i+1,len(A)):
                if (i,A[j]-A[i]) in dp:
                    dp[(j,A[j]-A[i])]  = 1+dp[(i,A[j]-A[i])]
                    del dp[(i,A[j]-A[i])]
                else: 
                    dp[(j,A[j]-A[i])] = 1
        maxx = 0
        ## we now find the maximum count
        for i in dp:
            if dp[i]>maxx: maxx = dp[i]
        return maxx+1
```