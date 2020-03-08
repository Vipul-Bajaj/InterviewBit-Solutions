<h1>Palindrome String</h1>

<p>Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

<b>Example :</b>
<br>

```python
"A man, a plan, a canal: Panama" is a palindrome.

"race a car" is not a palindrome.
```

Return 0 / 1 ( 0 for false, 1 for true ) for this problem

</p>
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return an integer
    def isPalindrome(self, A):
        A = A.upper()
    
        A = [i for i in A if (ord(i)>64 and ord(i)<91) or (ord(i)>47 and ord(i)<58)]
        
        A = "".join(A)
        
        if A == A[::-1]:
            return 1
        else:
            return 0
```