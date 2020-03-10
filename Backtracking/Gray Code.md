<h1>Gray Code</h1>

<p>
The gray code is a binary numeral system where two successive values differ in only one bit.

Given a non-negative integer n representing the total number of bits in the code, print the sequence of gray code. A gray code sequence must begin with 0.

For example, given n = 2, return [0,1,3,2]. Its gray code sequence is:

    00 - 0
    01 - 1
    11 - 3
    10 - 2
There might be multiple gray code sequences possible for a given n.
Return any such sequence.
</p>

<h2>Solution</h2>

***

```python
def binarytogray(n):
    return n^(n>>1)
class Solution:
    # @param A : integer
    # @return a list of integers
    def grayCode(self, A):
        res=[]
        for i in range(0,2**A):
            res.append(binarytogray(i))
        
        return res

```