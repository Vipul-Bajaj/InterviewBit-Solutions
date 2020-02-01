<h1>Power of 2</h1>

<p>
Find if Given number is power of 2 or not.
More specifically, find if given number can be expressed as 2^k where k >= 1.
</p>

<p><b>Example :</b>
<br>

```python
Input : 128
Output : 1
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return an integer
    def power(self, A):
        A = int(A)
        if A%2 == 1:
            return 0
        while A>1:
            A = A//2
            
            if A%2 == 1 and A!=1:
                return 0
            
        return 1
```