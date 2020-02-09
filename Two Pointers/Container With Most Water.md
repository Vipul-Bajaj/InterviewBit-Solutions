<h1>Container With Most Water</h1>

<p>
Given n non-negative integers a1, a2, ..., an,
where each represents a point at coordinate (i, ai).
'n' vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0).

Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Your program should return an integer which corresponds to the maximum area of water that can be contained ( Yes, we know maximum area instead of maximum volume sounds weird. But this is 2D plane we are working with for simplicity ).
</p>

<p><b>Example :</b>
<br>

```python
Input : [1, 5, 4, 3]
Output : 6

Explanation : 5 and 3 are distance 2 apart. So size of the base = 2. Height of container = min(5, 3) = 3. 
So total area = 3 * 2 = 6
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def maxArea(self, A):
        if len(A)<2:
            return 0
        l,h = 0,len(A)-1
        max_area = -2**31
        while l<=h:
            area = (h-l)*(min(A[h],A[l]))
            max_area = max(max_area,area)
            if A[l]<A[h]:
                l+=1
            else:
                h-=1
                
        return max_area
```