<h1>Single Number</h1>

<p>Given an array of integers, every element appears thrice except for one. Find that single one.

Note: Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?</p>

<p>
<b>Constraints :</b>

```python
2 <= N <= 5000000  
0 <= A[i] <= INT_MAX
```

</p>

<p>
<b>Example :</b>
<br>
Input Array A : [4 1 1 2 2 4 3 4 1 2]
<br>
Output : 3
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @return an integer
    def singleNumber(self, A):
        first = 0
        second = 0
        n = len(A)
        for i in A:
            first = (first^i) & ~second
            second = (second^i) & ~first
            
        return first
```