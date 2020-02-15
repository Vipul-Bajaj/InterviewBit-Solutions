<h1>Flip</h1>

<p>You are given a binary string(i.e. with characters 0 and 1) S consisting of characters S1, S2, …, SN. In a single operation, you can choose two indices L and R such that 1 ≤ L ≤ R ≤ N and flip the characters SL, SL+1, …, SR. By flipping, we mean change character 0 to 1 and vice-versa.

Your aim is to perform ATMOST one operation such that in final string number of 1s is maximised. If you don’t want to perform the operation, return an empty array. Else, return an array consisting of two elements denoting L and R. If there are multiple solutions, return the lexicographically smallest pair of L and R.

Notes:

    1. Pair (a, b) is lexicographically smaller than pair (c, d) if a < c or, if a == c and b < d.
</p>

<p>
<b>Example :</b>
<br>

    S = 010

    Pair of [L, R] | Final string
    _______________|_____________
    [1 1]          | 110
    [1 2]          | 100
    [1 3]          | 101
    [2 2]          | 000
    [2 3]          | 001

    We see that two pairs [1, 1] and [1, 3] give same number of 1s in final string. So, we return [1, 1].

    If S = 111

    No operation can give us more than three 1s in final string. So, we return empty array [].
</p>


<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return a list of integers
    def flip(self, A):
        A = list(A)
        n=len(A)
        max_so_far =  -2**31
        max_ending_here = 0
        start = 0
        end = 0
        s = 0
        
        n_1 = len([x for x in A if x == '1'])
        if n_1 == n:
            return []
        for i in range(0,n): 
      
            if A[i] == '0':
                max_ending_here += 1
            else:
                max_ending_here += -1
      
            if max_so_far < max_ending_here: 
                max_so_far = max_ending_here 
                start = s 
                end = i 
      
            if max_ending_here < 0: 
                max_ending_here = 0
                s = i+1
        
        return [start+1,end+1]
```