<html>
<h1>Add One To Number</h1>

<p>
Given a non-negative number represented as an array of digits,

add 1 to the number ( increment the number represented by the digits ).

The digits are stored such that the most significant digit is at the head of the list.

    NOTE: Certain things are intentionally left unclear in this question which you should practice asking the interviewer.
        For example, for this problem, following are some good questions to ask :
        Q : Can the input have 0’s before the most significant digit. Or in other words, is 0 1 2 3 a valid input?
        A : For the purpose of this question, YES
        Q : Can the output have 0’s before the most significant digit? Or in other words, is 0 1 2 4 a valid output?
        A : For the purpose of this question, NO. Even if the input has zeroes before the most significant digit.
</p>

<p>
<b>Example :</b>

    If the vector has [1, 2, 3]

    the returned vector should be [1, 2, 4]

    as 123 + 1 = 124.1
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return a list of integers
    def plusOne(self, A):
        n = len(A)
        
        A = [str(i) for i in A]
        num = int("".join(A))
        num = num+1
        A = []
        while num>0:
            r = num%10
            num//=10
            A.append(r)
            
        return A[::-1]
```
</html>
