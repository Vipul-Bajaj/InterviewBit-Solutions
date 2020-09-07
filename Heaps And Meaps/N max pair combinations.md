<h1>Maximum Sum Combinations</h1>

<p>
Given two arrays A & B of size N each.
Find the maximum N elements from the sum combinations (Ai + Bj) formed from elements in array A and B.

For example if A = [1,2], B = [3,4], then possible pair sums can be 1+3 = 4 , 1+4=5 , 2+3=5 , 2+4=6
and maximum 2 elements are 6, 5

Example:

    N = 4
    a[]={1,4,2,3}
    b[]={2,5,1,6}
    Maximum 4 elements of combinations sum are
    10   (4+6), 
    9    (3+6),
    9    (4+5),
    8    (2+6)
</p>

<h2>Solution</h2>

***

```python
import heapq
class Solution:
    # @param A : list of integers
    # @param B : list of integers
    # @return a list of integers
    def solve(self, A, B):
        pq = []
        n = len(A)
        A.sort()
        B.sort()
        
        s = set()
        
        s.add((n-1,n-1))
        heapq.heappush(pq,(-1*(A[-1]+B[-1]),(n-1,n-1)))
        ans= []
        for k in range(n):
            top = heapq.heappop(pq)
            ans.append(-1*top[0])
            
            i = top[1][0]
            j = top[1][1]
            
            if (i-1,j) not in s:
                s.add((i-1,j))
                heapq.heappush(pq,(-1*(A[i-1]+B[j]),(i-1,j)))
            if (i,j-1) not in s:
                s.add((i,j-1))
                heapq.heappush(pq,(-1*(A[i]+B[j-1]),(i,j-1)))
                
        return ans
```
