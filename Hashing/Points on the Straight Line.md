<h1>Points on the Straight Line</h1>

<p>Given n points on a 2D plane, find the maximum number of points that lie on the same straight line.

Sample Input :

    (1, 1)
    (2, 2)
Sample Output :

    2
You will be given 2 arrays X and Y. Each point is represented by (X[i], Y[i])
</p>

<h2>Solution</h2>

***

```python
from collections import defaultdict
class Solution:
    # @param A : list of integers
    # @param B : list of integers
    # @return an integer
    def maxPoints(self, A, B):
        n = len(A)
        output = 0
        if n <= 2: return n
        for i in range(n-1):
            slopeDict = defaultdict(int)
            dup = 0
            for j in range(n):
                if A[i] == A[j] and B[i] == B[j]:
                    dup += 1
                    continue
                elif A[i] == A[j]: slope = float("inf")
                elif B[i] == B[j]: slope = 0
                else:
                    slope = (float(B[i] - B[j])/float(A[i]-A[j]))
                slopeDict[slope] += 1
            if slopeDict:
                temp = max(slopeDict.values())
            else: temp = 0
            temp += dup
            if temp > output:
                output = temp
        return output
```
