<h1>Palindrome Integer</h1>

<p>
Determine whether an integer is a palindrome. Do this without extra space.

A palindrome integer is an integer x for which reverse(x) = x where reverse(x) is x with its digit reversed.
Negative numbers are not palindromic.
</p>

<p>
<b>Example :</b>
<br>

    Input : 12121
    Output : True

    Input : 123
    Output : False
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return an integer
    def isPalindrome(self, A):
        A = str(A)
        if A == A[::-1]:
            return 1
        return 0
```