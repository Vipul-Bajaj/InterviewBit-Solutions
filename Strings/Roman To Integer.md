<h1>Roman To Integer</h1>

<p>
Given a string A representing a roman numeral.
Convert A into integer.

A is guaranteed to be within the range from 1 to 3999.

NOTE: Read more details about roman numerals at Roman Numeric System
</p>

<p><b>Example :</b>
<br>

```python
Input 1:
    A = "XIV"
Output 1:
    14

Input 2:
    A = "XX"
Output 2:
    20
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return an integer
    def romanToInt(self, A):
        r_to_n = {"I":1,"V":5,"X":10,"L":50,"C":100,"D":500,"M":1000}
        num = 0
        i = 0
        n = len(A)
        while i<n-1:
            if (A[i]=="I" and A[i+1]=="V") or (A[i]=="I" and A[i+1]=="X") or (A[i]=="I" and A[i+1]=="L") or (A[i]=="I" and A[i+1]=="C") or (A[i]=="I" and A[i+1]=="D") or (A[i]=="I" and A[i+1]=="M"):
                num += abs(r_to_n[A[i+1]] - r_to_n[A[i]])
                i+=2
            elif (A[i]=="V" and A[i+1]=="X") or (A[i]=="V" and A[i+1]=="L") or (A[i]=="V" and A[i+1]=="C") or (A[i]=="V" and A[i+1]=="D") or (A[i]=="V" and A[i+1]=="M"):
                num += abs(r_to_n[A[i+1]] - r_to_n[A[i]])
                i+=2
            elif (A[i]=="X" and A[i+1]=="L") or (A[i]=="X" and A[i+1]=="C") or (A[i]=="X" and A[i+1]=="D") or (A[i]=="X" and A[i+1]=="M"):
                num += abs(r_to_n[A[i+1]] - r_to_n[A[i]])
                i+=2
            elif (A[i]=="L" and A[i+1]=="C") or (A[i]=="L" and A[i+1]=="D") or (A[i]=="L" and A[i+1]=="M"):
                num += abs(r_to_n[A[i+1]] - r_to_n[A[i]])
                i+=2
            elif (A[i]=="C" and A[i+1]=="D")or (A[i]=="C" and A[i+1]=="M"):
                num += abs(r_to_n[A[i+1]] - r_to_n[A[i]])
                i+=2
            elif A[i]=="D" and A[i+1]=="M":
                num += abs(r_to_n[A[i+1]] - r_to_n[A[i]])
                i+=2
            else:
                num += r_to_n[A[i]]
                i+=1
                
        
        if i==n-1:
            num += r_to_n[A[i]]
        
        return num
```