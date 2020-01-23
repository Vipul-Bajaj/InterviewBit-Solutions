<h1>Length of Last Word</h1>

<p>Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.

If the last word does not exist, return 0.

Note: A word is defined as a character sequence consists of non-space characters only.</p>

<p><b>Example :</b><br>Given s = "Hello World"<br>return 5 as length("World") = 5</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return an integer
    def lengthOfLastWord(self, A):
        A = A.strip().upper()

        n = len(A)
        s,e = 0,-1
        for j in range(n-1,-1,-1):
            if ord(A[j])< 65 or 90 < ord("A"):
                s = j+1
                break
            else:
                if e == -1:
                    e = j
        
        # if s == -1 and e == -1:
        #     return 0
        return e+1-s
```