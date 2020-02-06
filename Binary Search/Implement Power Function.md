<h1>Implement Power Function</h1>

<p>GImplement pow(x, n) % d.

In other words, given x, n and d,

find (xn % d)

Note that remainders on division cannot be negative.
In other words, make sure the answer you return is non negative.</p>

<p><b>For Example :</b>
<br>

```python
Input : x = 2, n = 3, d = 3
Output : 2

2^3 % 3 = 8 % 3 = 2.
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param x : integer
    # @param n : integer
    # @param d : integer
    # @return an integer
    def pow(self, x, n, d):
        if x == 0:
            return 0
        if n == 0:
            return 1
        ans = pow(x,n//2,d)
        if n%2==0:
            return (ans*ans)%d
        else:
            return (x*ans*ans)%d
            
```