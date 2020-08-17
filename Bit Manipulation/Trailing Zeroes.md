<h1>Trailing Zeroes</h1>

<p>
Given an integer A, count and return the number of trailing zeroes.

Problem Constraints

    1 <= A <= 10^9

Input Format:

    First and only argument is an integer A.
Output Format:

    Return an integer denoting the count of trailing zeroes.

Example:

    Input 1:
        A = 18
    Input 2:
        A = 8
    Output 1:
        1
    Output 2:
        3
    Explanation 1:
        18 in binary is represented as: 10010, there is 1 trailing zero.
    Explanation 2:
        8 in binary is represented as: 1000, there are 3 trailing zeroes.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return an integer
    def solve(self, A):
        c = 0
        while A%2==0:
            c+=1
            A=A>>1
        return  c
```