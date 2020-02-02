<h1>Reverse Bits</h1>

<p>Reverse the bits of an 32 bit unsigned integer A.</p>

<p>
<b>Example :</b>
<br>

```python
Example Input 1:
    A = 0
Example Output 1:
    0
Explanation 1:
        00000000000000000000000000000000  
=>      00000000000000000000000000000000
Example Input 2:
    A = 3
Example Output 2:
    3221225472
Explanation 2:
          00000000000000000000000000000011 
=>        11000000000000000000000000000000
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : unsigned integer
    # @return an unsigned integer
    def reverse(self, A):
        # Way 1
        # b = bin(A)[2:]
        # n = len(b)
        
        # b = "0"*(32-n) + b
        
        # b = b[::-1]
        
        # return int(b,2)
        
        # Way 2
        b = 0
        for i in range(32):
            k = A&1
            b <<= 1
            b |= k
            A >>= 1
            
        return b
```