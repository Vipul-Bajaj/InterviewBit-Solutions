<h1>Excel Column Number</h1>

<p>
Given a column title as appears in an Excel sheet, return its corresponding column number.
</p>

<p>
<b>Example :</b>
<br>

    A -> 1
    
    B -> 2
    
    C -> 3
    
    ...
    
    Z -> 26
    
    AA -> 27
    
    AB -> 28 
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return an integer
    def titleToNumber(self, A):
        n = len(A)-1
        ans = 0
        for i in A:
            ans += (ord(i)-64)*(26**n)
            n-=1
        
        return ans  
```