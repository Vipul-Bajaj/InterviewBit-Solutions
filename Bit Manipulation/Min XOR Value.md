<h1>Min XOR Value</h1>

<p>Given an integer array A of N integers, find the pair of integers in the array which have minimum XOR value. Report the minimum XOR value.</p>

<p>
<b>Example :</b>
<br>

```python
Example Input 1:
    A = [0, 2, 5, 7]
Example Output 1:
    2
Explanation:
    0 xor 2 = 2
Example Input 2:
    A = [0, 4, 7, 9]
Example Output 2:
    3
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def findMinXor(self, A):
        A.sort()
        n = len(A)
        val = 0
        min_xor = 2**31
        for i in range(n-1):
            val = A[i]^A[i+1]
            min_xor = min(val,min_xor)
            
        return min_xor
```