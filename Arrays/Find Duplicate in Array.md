<h1>Find Duplicate in Array</h1>

<p>Given a read only array of n + 1 integers between 1 and n, find one number that repeats in linear time using less than O(n) space and traversing the stream sequentially O(1) times.</p>

<p>
<b>Example :</b>
<br>
Given [3 4 1 4 1]
<br>
Output : 1
</p>

<p>If there are multiple possible answers ( like in the sample case above ), output any one.

If there is no duplicate, output -1</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @return an integer
    def repeatedNumber(self, A):
        n = len(A)
        A = list(A)
        for i in range(n):
            if A[abs(A[i])] <0:
                return abs(A[i])
            else:
                A[abs(A[i])] = -A[abs(A[i])]
                
        return -1
```