<h1>Single Number</h1>

<p>Given an array of integers, every element appears twice except for one. Find that single one.

Note: Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?</p>

<p>
<b>Constraints :</b>

```python
2 <= N <= 2000000  
0 <= A[i] <= INT_MAX
```

</p>

<p>
<b>Example :</b>
<br>
Input Array A : [4 1 1 2 2 4 3]
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
        res = 0
        for i in A:
            res^=i
            
        return res
```