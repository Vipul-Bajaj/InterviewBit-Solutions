<h1>Minimum Parantheses</h1>

<p>
Given a string A of parantheses ‘(‘ or ‘)’.

The task is to find minimum number of parentheses ‘(‘ or ‘)’ (at any positions) we must add to make the resulting parentheses string valid.

An string is valid if:

Open brackets must be closed by the corresponding closing bracket.
Open brackets must be closed in the correct order.

Problem Constraints

    1 <= |A| <= 10^5
    A[i] = '(' or A[i] = ')'
Input Format

    First and only argument is an string A.
Output Format
    
    Return a single integer denoting the minimumnumber of parentheses ‘(‘ or ‘)’ (at any positions) we must add in A to make the resulting parentheses string valid.

Example:

    Input 1:
        A = "())"
    Input 2:
        A = "((("
    Output 1:
        1
    Output 2:
        3
    Explanation 1:
        One '(' is required at beginning.
    Explanation 2:
        Three ')' is required at end.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return an integer
    def solve(self, A):
        st = []
        n = len(A)
        count=0
        for i in range(n):
            if A[i] == '(':
                st.append(A[i])
            else:
                if len(st)<=0:
                    count+=1
                else:
                    st.pop(-1)
        
        count+=len(st)
         
        return count
```