<h1>Sorted Permutation Rank</h1>

<p>
Given a string, find the rank of the string amongst its permutations sorted lexicographically.
Assume that no characters are repeated.

<b>Example :</b>

    Input : 'acb'
    Output : 2

    The order permutations with letters 'a', 'c', and 'b' : 
    abc
    acb
    bac
    bca
    cab
    cba
    The answer might not fit in an integer, so return your answer % 1000003
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return an integer
    def fact (self, n ) :
        if n <= 1 :
            return 1
        else :
            return n * self.fact(n-1)
    def findRank(self, A):
            res = 1
            for i in range(0, len(A)-1) :
                rank = 0
                for j in range(i+1, len(A)) :
                    if A[i] > A[j] :
                        rank += 1
                res = (res + rank * self.fact(len(A) - i - 1 ))%1000003
            return res
```