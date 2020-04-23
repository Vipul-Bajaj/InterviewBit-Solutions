<h1>Trailing Zeros in Factorial</h1>

<p>
Given an integer n, return the number of trailing zeroes in n!.

Note: Your solution should be in logarithmic time complexity.
</p>

<p>
<b>Example :</b>
<br>

    n = 5
    n! = 120 
    Number of trailing zeros = 1
    So, return 1
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return an integer
    def trailingZeroes(self, A):
        if A<5:
            return 0
        count=0
        while A>=5:
            count += A//5
            A//=5
            
        return count
```