<h1>Number of 1 Bits</h1>

<p>Write a function that takes an unsigned integer and returns the number of 1 bits it has.</p>

<p>
<b>Example :</b>
<br>
Input : 11

```python
The 32-bit integer 11 has binary representation 00000000000000000000000000001011
```
<br>
Output : 3
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return an integer
    def numSetBits(self, A):
        n = A
        s = 0
        while A>1:
            A = A>>1
            s += A
            
        return n-s
```