<h1>Subset II</h1>

<p>
Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses of length 2*n.

For example, given n = 3, a solution set is:

    "((()))", "(()())", "(())()", "()(())", "()()()"

Make sure the returned list of strings are sorted.
</p>

<h2>Solution</h2>

***

```python
def solve(res,openB,closeB,st):
    if openB == 0 and closeB == 0:
        res.append(st)
        return res
    if openB>closeB:
        return res
    if openB>0:
        solve(res,openB-1,closeB,st+"(")
    if closeB>0:
        solve(res,openB,closeB-1,st+")")
        
    return res
    
class Solution:
    # @param A : integer
    # @return a list of strings
    def generateParenthesis(self, A):
        res = solve([],A,A,"")
        return res
```