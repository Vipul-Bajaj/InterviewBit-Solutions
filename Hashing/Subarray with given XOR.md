<h1>Subarray with given XOR</h1>

<p>
Given an array of integers A and an integer B.
Find the total number of subarrays having bitwise XOR of all elements equals to B.

Problem Constraints:

    1 <= length of the array <= 105
    1 <= A[i] <= 109
Input Format:

    The first argument given is the integer array A.
    The second argument given is integer B.
Output Format:
    Return the total number of subarrays having bitwise XOR of all elements equals to B.
Example Input:

    Input 1:
        A = [4, 2, 2, 6, 4]
        B = 6
    Input 2:
        A = [5, 6, 7, 8, 9]
        B = 5
    Output 1:
        4
    Output 2:
        2
    Explanation 1:
        The subarrays having XOR of their elements as 6 are:
        [4, 2], [4, 2, 2, 6, 4], [2, 2, 6], [6]
    Explanation 2:
        The subarrays having XOR of their elements as 2 are [5] and [5, 6, 7, 8, 9]
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
        m = {}
        ans = 0
        xor = [0]*n
        xor[0] = A[0]
        
        for i in range(1,n):
            xor[i] = xor[i-1]^A[i]
            
        for i in range(n):
            tmp = B^xor[i]
            
            if tmp in m:
                ans +=m[tmp]
                
            if xor[i]==B:
                ans+=1
            
            m[xor[i]] = m.get(xor[i],0)+1
            
        return ans
```