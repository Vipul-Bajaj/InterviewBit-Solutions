<h1>Conunting Triangles</h1>

<p>
You are given an array of N non-negative integers, A0, A1 ,…, AN-1.
Considering each array element Ai as the edge length of some line segment, count the number of triangles which you can form using these array values.

Notes:

1. You can use any value only once while forming each triangle. Order of choosing the edge lengths doesn’t matter. Any triangle formed should have a positive area.
2. Return answer modulo 109 + 7.
</p>

<p><b>Example :</b>
<br>

```python
A = [1, 1, 1, 2, 2]
Return: 4
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
	# @param A : list of integers
	# @return an integer
	def nTriang(self, A):
        n = len(A)
        A.sort()
        c = 0
        for i in range(n - 1, 0, -1): 
            l = 0; 
            r = i - 1; 
            while(l < r): 
                if(A[l] + A[r] > A[i]): 
                    c += r - l;  
                    r -= 1;  
                else: 
                    l += 1;  
        return c%1000000007
```