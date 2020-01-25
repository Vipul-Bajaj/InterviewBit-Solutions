<h1>Multiply Strings</h1>

<p>
Given two numbers represented as strings, return multiplication of the numbers as a string.

 Note: The numbers can be arbitrarily large and are non-negative.
Note2: Your answer should not have leading zeroes. For example, 00 is not a valid answer. 

NOTE : DO NOT USE BIG INTEGER LIBRARIES ( WHICH ARE AVAILABLE IN JAVA / PYTHON ).
We will retroactively disqualify such submissions and the submissions will incur penalties.
</p>

<p><b>Example :</b><br>Input : A = "12" B="10"<br>Output : "120"</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : string
    # @return a strings
    def multiply(self, A, B):
        A = int(A)
        B = int(B)
        
        return str(A*B)
```