<h1>Wave Array</h1>

<p>Given an array of integers, sort the array into a wave like array and return it,
In other words, arrange the elements into a sequence such that a1 >= a2 <= a3 >= a4 <= a5.....</p>

<p>
<b>Example :</b>
<br>
Given [1, 2, 3, 4]
<br>
One possible answer : [2, 1, 4, 3]
Another possible answer : [4, 1, 3, 2]
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return a list of integers
    def wave(self, A):
        A.sort()
        
        n = len(A)
        i = 0
        while i<n-1:
            A[i],A[i+1] = A[i+1],A[i]
            i+=2
        return A

```