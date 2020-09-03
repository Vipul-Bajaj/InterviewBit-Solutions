<h1>Maximal String</h1>

<p>
Given a string A and integer B, what is maximal lexicographical stringthat can be made from A if you do atmost B swaps.

Problem Constraints:

    1 <= |A| <= 9
    A contains only digits from 0 to 9.
    1 <= B <= 5
Input Format:

    First argument is string A.
    Second argument is integer B.
    
Output Format:

    Return a string, the naswer to the problem.
    
Example Input:

    Input 1:
        A = "254"
        B = 1
    Input 2:
        A = "254'
        B = 2
    Output 1:
        524
    Output 2:
        542
    Explanation 1:
        Swap 2 and 5.
    Explanation 2:
        Swap 2 and 5 then swap 4 and 2.
</p>

<h2>Solution</h2>

***

```python
def getMax(A,B,index,ans):
    if B==0:
        return
    for i in range(index,len(A)-1):
        for j in range(i,len(A)):
            A[i],A[j] = A[j],A[i]
            if int("".join(A))>ans[0]:
                ans[0] = int("".join(A))
            getMax(A,B-1,index+1,ans)
            A[i],A[j] = A[j],A[i]
class Solution:
    # @param A : string
    # @param B : integer
    # @return a strings
    def solve(self, A, B):
        ans = [int(A)]
        getMax(list(A),B,0,ans)
        return ans[0]
```
