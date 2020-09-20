<h1>Largest Permutation</h1>

<p>
Given an integer array A of size N consisting of unique integers from 1 to N. You can swap any two integers atmost B times.

Return the largest lexicographical value array that can be created by executing atmost B swaps.

Problem Constraints

    1 <= N <= 10^6
    1 <= B <= 10^9

Input Format:

    First argument is an integer array A of size N.
    Second argument is an integer B.

Output Format:

    Return an integer array denoting the largest lexicographical value array that can be created by executing atmost B swaps

Example:

    Input 1:
        A = [1, 2, 3, 4]
        B = 1
    Input 2:
        A = [3, 2, 1]
        B = 2
    Output 1:
        [4, 2, 3, 1]
    Output 2:
        [3, 2, 1]
    Explanation 1:
        In one swap we can swap (1, 4) so that the array becomes : [4, 2, 3, 1].
    Explanation 2:
        Array is already the largest lexicographical value array.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return a list of integers
    def solve(self, A, B):
        n = len(A)
        m = {}
        for i in range(n):
            m[A[i]] = i
        
        for i in range(n):
            if B>0:
                if A[i]!=n-i:
                    B-=1
                    m[A[i]] = m[n-i]
                    A[m[n-i]] = A[i]
                    m[n-i] = i
                    A[i] = n-i
            else:
                break
        
        return A
```
