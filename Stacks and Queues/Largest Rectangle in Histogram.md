<h1>Largest Rectangle in Histogram</h1>

<p>Given an array of integers A of size N. A represents a histogram i.e A[i] denotes height of
the ith histogram’s bar. Width of each bar is 1.

<p><img src="http://i.imgur.com/1OutEEI.png" alt="Largest Rectangle in Histogram: Example 1"></p>

Above is a histogram where width of each bar is 1, given height = [2,1,5,6,2,3].

<p><img src="http://i.imgur.com/F2bePvG.png" alt="Largest Rectangle in Histogram: Example 2"></p>

The largest rectangle is shown in the shaded area, which has area = 10 unit.

Find the area of largest rectangle in the histogram.</p>

<p><b>Example :</b>
<br>

```python
Input 1:
    A = [2, 1, 5, 6, 2, 3]
Output 1:
    10
    Explanation 1:
        The largest rectangle is shown in the shaded area, which has area = 10 unit.
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def largestRectangleArea(self, A):
        st = []
        n = len(A)
        max_area = -2**31
        i=0
        while i<n:
            while st and A[st[-1]]>A[i]:
                x = st.pop(-1)
                if st:
                    max_area = max(max_area,A[x]*(i-st[-1]-1))
                else:
                    max_area = max(max_area,A[x]*i)
            st.append(i)
            i+=1
            
        while st:
                x = st.pop(-1)
                if st:
                    max_area = max(max_area,A[x]*(i-st[-1]-1))
                else:
                    max_area = max(max_area,A[x]*i)
        return max_area
```