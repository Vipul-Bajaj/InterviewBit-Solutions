<h1>Merge K sorted arrays</h1>

<p>
You are given K sorted integer arrays in a form of 2D integer matrix A of size K X N.

You need to merge them into a single array and return it.

Problem Constraints:

    1 <= K, N <= 10^3
    0 <= A[i][j] <= 10^8
    A[i][j] <= A[i][j+1]

Input Format:

    First and only argument is an 2D integer matrix A.
    
Output Format:

    Return a integer array denoting the merged array you get after merging all the arrays in A.
Example Input:

    Input 1:
        A = [  [1, 2, 3]
               [2, 4, 6]
               [0, 9, 10]
            ]
    Output 1:
        [0, 1, 2, 2, 3, 4, 6, 9, 10]
    Explanation 1:
        You need to merge [1, 2, 3] , [2, 4, 6] and [0, 9, 10]  into a single array
        so the merged array will look like [0, 1, 2, 2, 3, 4, 6, 9, 10]
</p>

<h2>Solution</h2>

***

```python
from heapq import heappush,heappop
def mergeKArrays(A):
    pq=[]
    output=[]
    for i in range(len(A)):
        heappush(pq,(A[i][0],i,0))
    while(len(pq)!=0):
        a,b,c=heappop(pq)
        i=b
        j=c
        output.append(a)
        if(j+1<len(A[i])):
            heappush(pq,(A[i][j+1],i,j+1))
    return output
class Solution:
    # @param A : list of list of integers
    # @return a list of integers
    def solve(self, A):
        return mergeKArrays(A)
```
