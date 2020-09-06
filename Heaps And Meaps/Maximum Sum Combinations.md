<h1>Maximum Sum Combinations</h1>

<p>
Given two equally sized 1-D arrays A, B containing N integers each.
A sum combination is made by adding one element from array A and another element of array B.

Return the maximum C valid sum combinations from all the possible sum combinations.

Problem Constraints:

    1 <= N <= 10^5
    1 <= A[i] <= 10^3
    1 <= C <= N

Input Format:

    First argument is an one-dimensional integer array A of size N.
    Second argument is an one-dimensional integer array B of size N.
    Third argument is an integer C.
    
Output Format:

    Return a one-dimensional integer array of size C denoting the top C maximum sum combinations.
    NOTE:
        The returned array must be sorted in non-increasing order.
Example Input:

    Input 1:
        A = [3, 2]
        B = [1, 4]
        C = 2
    Input 2:
        A = [1, 4, 2, 3]
        B = [2, 5, 1, 6]
        C = 4
    Output 1:
        [7, 6]
    Output 2:
        [10, 9, 9, 8]
    Explanation 1:
        7     (A : 3) + (B : 4)
        6     (A : 2) + (B : 4)
    Explanation 2:
        10   (A : 4) + (B : 6)
         9   (A : 4) + (B : 5)
         9   (A : 3) + (B : 6)
         8   (A : 3) + (B : 5)
</p>

<h2>Solution</h2>

***

```python
import heapq
class Solution:
    # @param A : list of integers
    # @param B : list of integers
    # @param C : integer
    # @return a list of integers
    def solve(self, A, B, C):
        pq = []
        n = len(A)
        A.sort()
        B.sort()
        
        s = set()
        
        s.add((n-1,n-1))
        heapq.heappush(pq,(-1*(A[-1]+B[-1]),(n-1,n-1)))
        ans= []
        for k in range(C):
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
