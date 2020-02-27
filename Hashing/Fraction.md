<h1>Fraction</h1>

<p>Given two integers representing the numerator and denominator of a fraction, return the fraction in string format.

If the fractional part is repeating, enclose the repeating part in parentheses.</p>

<p><b>Example :</b>
<br>

    Given numerator = 1, denominator = 2, return "0.5"
    Given numerator = 2, denominator = 1, return "2"
    Given numerator = 2, denominator = 3, return "0.(6)"
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @param B : integer
    # @return a strings
    def fractionToDecimal(self, A, B):
        numerator,denominator=A,B
        if denominator == 0:
            return "NaN"
            
        if numerator * denominator < 0:
            neg = True
        else:
            neg = False
        
        numerator = abs(numerator)
        denominator = abs(denominator)
        s = str(numerator/denominator)
        
        remainder = numerator%denominator
        
        if remainder:
            s += '.'
        
        d = {}
        
        #d[remainder] = len(s)
        
        i = len(s)
        while remainder:
            numerator = remainder * 10
            digit = str(numerator/denominator)
            
            if remainder in d:
                s = s[:d[remainder]]+ "(" + s[d[remainder]:] + ")"
                break
            else:
                s += digit
                d[remainder] = i
            
            remainder = numerator%denominator
            i += 1
        
        return s if not neg else "-"+s
```
