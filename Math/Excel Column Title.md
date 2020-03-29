<h1>Excel Column Title</h1>

<p>
Given a positive integer, return its corresponding column title as appear in an Excel sheet.
</p>

<p>
<b>Example :</b>
<br>

    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return a strings
    def convertToTitle(self, A):
        ans = ""
        while A>0:
            r = A%26
            A//=26
            if r==0:
                r=26
                A-=1
            
            ans = chr(r+64) + ans
        
        return ans
```