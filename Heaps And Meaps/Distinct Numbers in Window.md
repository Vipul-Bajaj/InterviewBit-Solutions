<h1>Distinct Numbers in Window</h1>

<p>
You are given an array of N integers, A1, A2 ,…, AN and an integer K. Return the of count of distinct numbers in all windows of size K.

Formally, return an array of size N-K+1 where i’th element in this array contains number of distinct elements in sequence Ai, Ai+1 ,…, Ai+k-1.

Note:

    If K > N, return empty array.
    A[i] is a signed integer

For example,

    A=[1, 2, 1, 3, 4, 3] and K = 3

    All windows of size K are

    [1, 2, 1]
    [2, 1, 3]
    [1, 3, 4]
    [3, 4, 3]

    So, we return an array [2, 3, 3, 2].
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return a list of integers
    def dNums(self, A, B):
        hm = {}
        n = len(A)
        dist = 0
        ans = []
        for i in range(0,B):
            if A[i] in hm:
                hm[A[i]]+=1
            else:
                hm[A[i]]=1
                dist+=1

        for i in range(B,n):
            ans.append(dist)
            if hm[A[i-B]] > 1:
                hm[A[i-B]]-=1
            else:
                del hm[A[i-B]]
                dist-=1
                
            if A[i] in hm:
                hm[A[i]]+=1
            else:
                hm[A[i]]=1
                dist+=1
                
        ans.append(dist)
        
        return ans
```