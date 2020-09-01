<h1>Subarrays With Distinct Integers</h1>

<p>
Given an array A of positive integers,call a (contiguous,not necessarily distinct) subarray of A good if the number of different integers in that subarray is exactly B.

(For example: [1, 2, 3, 1, 2] has 3 different integers 1, 2 and 3)

Return the number of good subarrays of A.

Problem Constraints:

    1 <= |A| <= 40000
    1 <= A[i] <= |A|
    1 <= B <= |A|
Input Format:

    The first argument given is the integer array A.
    The second argument given is an integer B.

Output Format:

    Return an integer denoting the number of good subarrays of A.
Example Input:

    Input 1:
        A = [1, 2, 1, 2, 3]
        B = 2
    Input 2:
        A = [1, 2, 1, 3, 4]
        B = 3
    Output 1:
        7
    Output 2:
        3
    Explanation 1:
        Subarrays formed with exactly 2 different integers: [1, 2], [2, 1], [1, 2], [2, 3], [1, 2, 1], [2, 1, 2], [1, 2, 1, 2].
    Explanation 2:
        Subarrays formed with exactly 3 different integers: [1, 2, 1, 3], [2, 1, 3], [1, 3, 4].
</p>

<h2>Solution</h2>

***

```python
def solve(A,B):
    n = len(A)
    
    count = 0
    left,right = 0,0
    h = {}
    
    while right<n:
        if A[right] not in h:
            h[A[right]] = 0
        h[A[right]]+=1
        while len(h)>B:
            if A[left] not in h:
                h[A[left]]=0
            h[A[left]]-=1
            
            if h[A[left]] == 0:
                del h[A[left]]
            left+=1
        count += right-left+1
        right+=1
    
    return count
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return an integer
    def solve(self, A, B):
        return solve(A,B)-solve(A,B-1)
```