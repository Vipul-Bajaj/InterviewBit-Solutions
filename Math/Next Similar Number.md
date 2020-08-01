<h1>Next Similar Number</h1>

<p>
Given a number A in a form of string.

You have to find the smallest number that has same set of digits as A and is greater than A.

If A is the greatest possible number with its set of digits, then return -1.

Problem Constraints

    1 <= A <= 10^100000
    A doesn't contain leading zeroes.
Input Format

    First and only argument is an numeric string denoting the number A.
Output Format
    
    Return a string denoting the smallest number greater than A with same set of digits , if A is the largest possible then return -1.
Example:

    Input 1:
        A = "218765"
    Input 2:
        A = "4321"
    Output 1:
        "251678"
    Output 2:
        "-1"
    Explanation 1:
        The smallest number greater then 218765 with same set of digits is 251678.
    Explanation 2:
        The given number is the largest possible number with given set of digits so we will return -1.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return a strings
    def solve(self, A):
        A = list(A)
        A = [int(x) for x in A]
        n = len(A)
        i = n-1
        while i>0 and A[i-1]>=A[i]:
            i-=1
        if i<=0:
            return "-1"
            
        j = n-1
        
        while A[j]<= A[i-1]:
            j-=1
            
        A[i-1],A[j] = A[j],A[i-1]
        
        A[i : ] = A[n - 1 : i - 1 : -1]
        
        A = [str(x) for x in A]
        return "".join(A)
```