<h1>Evaluate Expression</h1>

<p>Evaluate the value of an arithmetic expression in Reverse Polish Notation.

Valid operators are +, -, *, /. Each operand may be an integer or another expression.</p>

<p><b>Example :</b>
<br>

```python
Input 1:
    A =   ["2", "1", "+", "3", "*"]
Output 1:
    9
Explaination 1:
    starting from backside:
    *: ( )*( )
    3: ()*(3)
    +: ( () + () )*(3)
    1: ( () + (1) )*(3)
    2: ( (2) + (1) )*(3)
    ((2)+(1))*(3) = 9
    
Input 2:
    A = ["4", "13", "5", "/", "+"]
Output 2:
    6
Explaination 2:
    +: ()+()
    /: ()+(() / ())
    5: ()+(() / (5))
    1: ()+((13) / (5))
    4: (4)+((13) / (5))
    (4)+((13) / (5)) = 6
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of strings
    # @return an integer
    def evalRPN(self, A):
        operand = []
    
        for i in A:
            if i not in ["+","*","/","-"]:
                operand.append(i)
            else:
                a = int(operand.pop(-1))
                b = int(operand.pop(-1))
                if i == "+":
                    c = a+b
                if i == "-":
                    c = b-a
                if i == "*":
                    c = a*b
                if i == "/":
                    c = b//a
                operand.append(str(c))
                    
        return int(operand[-1])
```