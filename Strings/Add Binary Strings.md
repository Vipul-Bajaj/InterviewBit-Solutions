<h1>Add Binary Strings</h1>

<p>Given two binary strings, return their sum (also a binary string).</p>

<p><b>Example :</b>
<br>
a = "100"
b = "11"
<br>
Return a + b = “111”.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : string
    # @return a strings
    def addBinary(self, A, B):
        # A = int(A,2)
        # B = int(B,2)
        # C = A+B
        # return bin(C)[2:]
        
        m,n = len(A),len(B)
        i,j = m-1,n-1
        s = ""
        c = "0"
        while i>=0 and j>=0:
            if A[i] == '0' and B[j] == '0':
                if c == '0':
                    s = "0" + s
                    c = "0"
                else:
                    s = "1" + s
                    c = "0"
            elif (A[i] == '1' and B[j] == '0') or (A[i] == '0' and B[j] == '1'):
                if c == '0':
                    s = "1" + s
                    c = "0"
                else:
                    s = "0" + s
                    c = "1"
            else:
                if c == '0':
                    s = "0" + s
                    c = "1"
                else:
                    s = "1" + s
                    c = "1"
            
            i-=1
            j-=1
        
        
        while i>=0:
            if (A[i]=='0' and c=='1') or (A[i]=='1' and c=='0'):
                s = "1"+ s
                c = '0'
            elif A[i]=='0' and c=='0':
                s = "0"+ s
                c = '0'
            elif A[i]=='1' and c=='1':
                s = "0"+ s
                c = '1'
            i-=1
            
        while j>=0:
            if (B[j]=='0' and c=='1') or (B[j]=='1' and c=='0'):
                s = "1"+ s
                c = '0'
            elif B[j]=='0' and c=='0':
                s = "0"+ s
                c = '0'
            elif B[j]=='1' and c=='1':
                s = "0"+ s
                c = '1'
            j-=1
                
        if c == '1':
            s = c + s
        return s
```