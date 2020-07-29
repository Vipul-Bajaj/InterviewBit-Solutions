<h1>Remove Consecutive Characters</h1>

<p>
Given a string A and integer B, remove all consecutive same characters that have length exactly B.

Problem Constraints

    1 <= |A| <= 100000
    1 <= B <= |A|
Input Format

    First Argument is string A.
    Second argument is integer B.
Output Format
    
    Return a string after doing the removals.

Example:

    Input 1:
        A = "aabcd"
        B = 2
    Input 2:
        A = "aabbccd"
        B = 2
    Output 1:
        "bcd"
    Output 2:
        "d"
    Explanation 1:
        "aa" had length 2.
    Explanation 2:
        "aa", "bb" and "cc" had length of 2.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : integer
    # @return a strings
    def solve(self, A, B):
        A = list(A)
        n = len(A)
        curr_ch = A[0]
        curr_count = 1
        start = 0
        end = start+1
        S = []
        for i in range(1,n):
            if A[i] == curr_ch:
                curr_count+=1
            else:
                if curr_count == B:
                    start = i
                    end = start+1
                else:
                    S += A[start:end]
                    start = end
                    end = start+1
                curr_ch = A[i]
                curr_count = 1
                    
        if curr_count != B:
            S += A[start:]
        return ''.join(S)
```