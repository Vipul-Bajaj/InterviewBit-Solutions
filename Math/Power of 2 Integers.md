<h1>Power of 2 Integers</h1>

<p>
Given a positive integer which fits in a 32 bit signed integer, find if it can be expressed as A^P where P > 1 and A > 0. A and P both should be integers.
</p>

<p>
<b>Example :</b>
<br>

    Input : 4
    Output : True  
    as 2^2 = 4. 
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return an integer
    def isPower(self, A):
        from math import log, sqrt
        if A==1:
            return 1
        
        for i in range(2,int(sqrt(A))+1):
            x=round(log(A,i),5)
            if x%1==0:
                return 1
                
        return 0
```