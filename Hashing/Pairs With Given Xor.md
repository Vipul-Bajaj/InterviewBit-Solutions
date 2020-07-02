<h1>Pairs With Given Xor</h1>

<p>
Given an 1D integer array A containing N distinct integers.
Find the number of unique pairs of integers in the array whose XOR is equal to B.

NOTE:

    Pair (a, b) and (b, a) is considered to be same and should be counted once.


Problem Constraints
    
    1 <= N <= 105
    1 <= A[i], B <= 107
Input Format

    First argument is an 1D integer array A.
    Second argument is an integer B.
Output Format

    Return a single integer denoting the number of unique pairs of integers in the array A whose XOR is equal to B.
Example Input

    Input 1:
        A = [5, 4, 10, 15, 7, 6]
        B = 5
    Input 2:
        A = [3, 6, 8, 10, 15, 50]
        B = 5
    Output 1:
        1
    Output 2:
        2
    Explanation 1:
        (10 ^ 15) = 5
    Explanation 2:
        (3 ^ 6) = 5 and (10 ^ 15) = 5 
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return an integer
    def solve(self, A, B):
        hash_map = {}
        for i in A:
            if i in hash_map:
                hash_map[i]+=1
            else:
                hash_map[i] = 1
        count = 0        
        for i in A:
            x = i^B
            if x in hash_map:
                count+=1
                hash_map[i]-=1
                hash_map[x]-=1
                if hash_map[i] <= 0:
                    del hash_map[i]
                if hash_map[x] <= 0:
                    del hash_map[x]
        return count
```