<h1>Word Break II</h1>

<p>
Given a string A and a dictionary of words B, add spaces in A to construct a sentence where each word is a valid dictionary word.

Return all such possible sentences.

    Note : Make sure the strings are sorted in your result.

Input Format:

    The first argument is a string, A.
    The second argument is an array of strings, B.
Output Format:

    Return a vector of strings representing the answer as described in the problem statement.
Constraints:

    1 <= len(A) <= 6500
    1 <= len(B) <= 10000
    1 <= len(B[i]) <= 20

Examples:

    Input 1:
        A = "b"
        B = ["aabbb"]

    Output 1:
        []

    Input 1:
        A = "catsanddog",
        B = ["cat", "cats", "and", "sand", "dog"]

    Output 1:
        ["cat sand dog", "cats and dog"]                       
<h2>Solution</h2>

***

```python
def solve(A,B,prefix,res):
    for i in range(1,len(A)+1):
    
        s = A[0:i]

        if s in B:
            if i == len(A):
                prefix+=s
                res.append(prefix)
                return
            else:
                solve(A[i:],B,prefix+s+" ",res)
class Solution:
    # @param A : string
    # @param B : list of strings
    # @return a list of strings
    def wordBreak(self, A, B):
        res = []
        solve(A,B,"",res)
        return sorted(res)
```