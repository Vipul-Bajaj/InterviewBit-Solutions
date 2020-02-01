<h1>Maximum Absolute Difference</h1>

<p>You are given an array of N integers, A1, A2 ,…, AN. Return maximum value of f(i, j) for all 1 ≤ i, j ≤ N.
f(i, j) is defined as |A[i] - A[j]| + |i - j|, where |x| denotes absolute value of x.</p>

<p>
<b>Example :</b>
<br>
Given A=[1, 3, -1]
<br>
f(1, 1) = f(2, 2) = f(3, 3) = 0
f(1, 2) = f(2, 1) = |1 - 3| + |1 - 2| = 3
f(1, 3) = f(3, 1) = |1 - (-1)| + |1 - 3| = 4
f(2, 3) = f(3, 2) = |3 - (-1)| + |2 - 3| = 5

So, we return 5.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def maxArr(self, A):
        n = len(A)
        max1,max2,max3,max4 = -2**31,-2**31,-2**31,-2**31
        min1,min2,min3,min4 = 2**31,2**31,2**31,2**31
        
        for i in range(n):
            max1 = max(max1,A[i]+i)
            max2 = max(max2,A[i]-i)
            max3 = max(max3,-A[i]+i)
            max4 = max(max4,-A[i]-i)
            
            min1 = min(min1,A[i]+i)
            min2 = min(min2,A[i]-i)
            min3 = min(min3,-A[i]+i)
            min4 = min(min4,-A[i]-i)
            
        
        ans = max1-min1
        ans = max(ans,max2-min2)
        ans = max(ans,max3-min3)
        ans = max(ans,max4-min4)
        
        return ans

```