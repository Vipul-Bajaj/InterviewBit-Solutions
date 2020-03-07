<h1>Integer To Roman</h1>

<p>
Given an integer A, convert it to a roman numeral, and return a string corresponding to its roman numeral version
</p>

<p><b>Example :</b>
<br>

```python
Input 1:
    A = 5
Output 1:
    "V"

Input 2:
    A = 14
Output 2:
    "XIV"
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return a strings
    def intToRoman(self, A):
        A = int(A)
        num = [1, 4, 5, 9, 10, 40, 50, 90,  
               100, 400, 500, 900, 1000] 
        sym = ["I", "IV", "V", "IX", "X", "XL",  
               "L", "XC", "C", "CD", "D", "CM", "M"] 
        i = 12
        s = ""
        while A: 
            div = A // num[i] 
            A %= num[i] 
      
            while div: 
                s += sym[i]
                div -= 1
            i -= 1
        return s
```