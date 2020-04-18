<h1>Palindrome Integer</h1>

<p>
Reverse digits of an integer.
</p>

<p>
<b>Example :</b>
<br>

    Input 1:
        x = 123,
    Output 1:
        return 321

    Input 2:
        x = -123,
    Output 2:
        return -321
Return 0 if the result overflows and does not fit in a 32 bit signed integer
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return an integer
    def reverse(self, A):
        if A<0:
            A = A*-1
            A = str(A)
            A=A[::-1]
            A = int(A)
            A = -1*A
        else:
            A = str(A)
            A=A[::-1]
            A = int(A)
        
        if A>2**31-1 or A<-2**31:
            return 0
        return A
```