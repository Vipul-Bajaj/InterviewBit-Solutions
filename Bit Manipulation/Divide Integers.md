<h1>Divide Integers</h1>

<p>Divide two integers without using multiplication, division and mod operator.

Return the floor of the result of the division.</p>

<p>
<b>Example :</b>
<br>

```python
5 / 2 = 2
```
</p>

Also, consider if there can be overflow cases. For overflow case, return INT_MAX.

Note: INT_MAX = 2^31 - 1

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @param B : integer
    # @return an integer
    def divide(self, A, B):
        INT_MAX = 2**31 - 1
        sign = -1 if ((A < 0) ^  (B < 0)) else 1   
        A = abs(A); 
        B = abs(B); 
        quotient = 0; 
        temp = 0; 
    
        for i in range(31, -1, -1): 
            if (temp + (B << i) <= A): 
                temp += B << i; 
                quotient |= 1 << i; 
          
        if sign*quotient> INT_MAX:
            return INT_MAX
        return sign * quotient; 

```