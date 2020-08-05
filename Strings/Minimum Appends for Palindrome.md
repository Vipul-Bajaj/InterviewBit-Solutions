<h1>Minimum Appends for Palindrome</h1>

<p>
Given a string A consisting of lowercase characters.

We need to tell minimum characters to be appended (insertion at end) to make the string A a palindrome.

Problem Constraints

    1 <= |A| <= 10^5
Input Format

    First and only argument is an string A.
Output Format
    
    Return a integer denoting the minimum characters to be appended (insertion at end) to make the string A a palindrome.

Example:

    Input 1:
        A = "abede"
    Input 2:
        A = "aabb"
    Output 1:
        2
    Output 2:
        2
    Explanation 1:
        We can make string palindrome as "abedeba" by adding ba at the end of the string.
    Explanation 2:
        We can make string palindrome as "aabbaa" by adding aa at the end of the string.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return an integer
    def solve(self, A):
        n = len(A)
        A = A[::-1] + "$" + A
        lps = [0]*len(A)
        j = 0
        i = 1
    
        while i < len(A): 
            if A[i]== A[j]: 
                j += 1
                lps[i] = j
                i += 1
            else: 
                if j != 0: 
                    j = lps[j-1] 
                else: 
                    lps[i] = 0
                    i += 1 
                    
        return n - lps[-1]
```