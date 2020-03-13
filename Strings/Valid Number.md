<h1>Valid Number</h1>

<p>Validate if a given string is numeric.

```python
"0" => true
" 0.1 " => true
"abc" => false
"1 a" => false
"2e10" => true
```

Return 0 / 1 ( 0 for false, 1 for true ) for this problem

<b>NOTE: Good clarification questions:</b>

```python
Q1. Is 1u ( which may be a representation for unsigned integers valid?
A. For this problem, no.
Q2. Is 0.1e10 valid?
A. Yes
Q3. -01.1e-10?
A. Yes
Q4. Hexadecimal numbers like 0xFF?
A. Not for the purpose of this problem
Q5. 3. (. not followed by a digit)?
A. No
Q6. Can exponent have decimal numbers? 3e0.1?
A. Not for this problem.
Q7. Is 1f ( floating point number with f as prefix ) valid?
A. Not for this problem.
Q8. How about 1000LL or 1000L ( C++ representation for long and long long numbers )?
A. Not for this problem.
Q9. How about integers preceded by 00 or 0? like 008?
A. Yes for this problem
```
</p>
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return an integer
    def isNumber(self, A):
        A = A.strip()
        n = len(A)
        dot = A.find(".")
        if dot == n-1:
            return 0
        elif ord(A[dot+1]) <48 or ord(A[dot+1])>57:
            return 0
        try:
            float(A)
            return 1
        except Exception:
            return 0
```