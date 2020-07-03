<h1>Subarray with B odd numbers</h1>

<p>
Given an array of integers A and an integer B.
Find the total number of subarrays having exactly B odd numbers.

Problem Constraints:

    1 <= length of the array <= 105
    1 <= A[i] <= 109
    0 <= B <= A
Input Format:

    The first argument given is the integer array A.
    The second argument given is integer B.
Output Format:
    Return the total number of subarrays having exactly B odd numbers.
Example Input:

    Input 1:
        A = [4, 3, 2, 3, 4]
        B = 2
    Input 2:
        A = [5, 6, 7, 8, 9]
        B = 3
    Output 1:
        4
    Output 2:
        1
    Explanation 1:
        The subarrays having exactly B odd numbers are:
        [4, 3, 2, 3], [4, 3, 2, 3, 4], [3, 2, 3], [3, 2, 3, 4]
    Explanation 2:
        The subarrays having exactly B odd numbers is [5, 6, 7, 8, 9]
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
        prefix = [0] * n
        odd = 0
        count=0
        for i in range(n):
            prefix[odd]+=1
            
            if A[i]%2==1:
                odd+=1
            
            if odd>=B:
                count+=prefix[odd-B] if odd-B>=0 and odd-B <n else 0
                
        return count
```