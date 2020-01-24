<h1>Reverse the String</h1>

<p>
Given a string A.

Return the string A after reversing the string word by word.

NOTE:

1. A sequence of non-space characters constitutes a word.

2. Your reversed string should not contain leading or trailing spaces, even if it is present in the input string.

3. If there are multiple spaces between words, reduce them to a single space in the reversed string.

</p>

<p><b>Example :</b><br>Input : A = "the sky is blue"<br>Output : "blue is sky the"</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return a strings
    def solve(self, A):
        A = A.split(" ")
        
        A = A[::-1]
        
        return " ".join(A)

```