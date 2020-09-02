<h1>Maximum Ones After Modification</h1>

<p>
Given a binary array A and a number B, we need to find length of the longest subsegment of ‘1’s possible by changing at most B ‘0’s.

Problem Constraints:

    1 <= N, B <= 10^5
    A[i]=0 or A[i]=1
Input Format:

    First argument is an binary array A.
    Second argument is an integer B.
    
Output Format:

    Return a single integer denoting the length of the longest subsegment of ‘1’s possible by changing at most B ‘0’s.
    
Example Input:

    Input 1:
        A = [1, 0, 0, 1, 1, 0, 1]
        B = 1
    Input 2:
        A = [1, 0, 0, 1, 0, 1, 0, 1, 0, 1]
        B = 2
    Output 1:
        4
    Output 2:
        5
    Explanation 1:
        Here, we should only change 1 zero(0). Maximum possible length we can get is by changing the 3rd zero in the array,
        we get a[] = {1, 0, 0, 1, 1, 1, 1}
    Explanation 2:
        Here, we can change only 2 zeros. Maximum possible length we can get is by changing the 3rd and 4th (or) 4th and 5th zeros.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return an integer
    def solve(self, A, B):
        n = len(A)
        left = 0
        count = 0
        window = 0
        
        leftIndex = 0
        
        for right in range(n):
            if A[right] == 0:
                count = count + 1
            while count > B:
                if A[left] == 0:
                    count = count - 1
                left = left + 1
            if right - left + 1 > window:
                window = right - left + 1
                leftIndex = left
        
        return window
```
