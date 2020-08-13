<h1>Subarray with equal occurences!</h1>

<p>
Given an integer array A and two integers B and C.

You need to find the number of subarrays in which the number of occurrences of B is equal to number of occurrences of C.

NOTE: Don't count empty subarrays.

Problem Constraints
    
    1 <= |A| <= 10^4
    1 <= A[i], B, C <= 10^8
    B != C
Input Format

    First argument is an integer array A.
    Second argument is an integer B.
    Third argument is an integer C.
Output Format

    Return an integer denoting the number of subarrays in which the number of occurrences of B is equal to number of occurrences of C
Example Input

    Input 1:
        A = [1, 2, 1]
        B = 1
        C = 2
    Input 2:
        A = {1, 2, 1}
        B = 4
        C = 6
    Output 1:
        2
    Output 2:
        6
    Explanation 1:
        The possible sub-arrays have same equal number of occurrences of B and C are:
            1. {1, 2}, B and C have same occurrence(1).
            2. {2, 1}, B and C have same occurrence(1).
    Explanation 2:
        The possible sub-arrays have same equal number of occurrences of B and C are:
            1) {1}, B and C have same occurrence(0).
            2) {2}, B and C have same occurrence(0).
            3) {1}, B and C have same occurrence(0).
            4) {1, 2}, B and C have same occurrence(0).
            5) {2, 1}, B and C have same occurrence(0).
            6) {1, 2, 1}, B and C have same occurrence(0).
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @param C : integer
    # @return an integer
    def solve(self, A, B, C):
        n = len(A
        ans = 0
        for i in range(n):
            b = 0
            c = 0
            for j in range(i, n):
                if A[j] == B:
                    b += 1
                if A[j] == C:
                    c += 1
                if c == b:
                    ans += 1
        return ans
```