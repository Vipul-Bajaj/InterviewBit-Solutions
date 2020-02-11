<h1>Redundant Braces</h1>

<p>Given a string A denoting an expression. It contains the following operators ’+’, ‘-‘, ‘*’, ‘/’.

Chech whether A has redundant braces or not.

Return 1 if A has redundant braces, else return 0.

Note: A will be always a valid expression.</p>

<p><b>Example :</b>
<br>

```python
Input 1:
    A = "((a + b))"
Output 1:
    1
    Explanation 1:
        ((a + b)) has redundant braces so answer will be 1.

Input 2:
    A = "(a + (a + b))"
Output 2:
    0
    Explanation 2:
        (a + (a + b)) doesn't have have any redundant braces so answer will be 0.
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return an integer
    def braces(self, A):
        opr = []
        braces = []
        n = len(A)
        for i in range(n):
            if A[i] == "+" or A[i] == "-" or A[i] == "*" or A[i] == "/":
                opr.append(A[i])
            elif A[i] == "(":
                braces.append(A[i])
        
        if len(braces)>len(opr):
            return 1
        return 0
```