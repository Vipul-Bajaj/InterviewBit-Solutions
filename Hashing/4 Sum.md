<h1>4 Sum</h1>

<p>Given an array S of n integers, are there elements a, b, c, and d in S such that a + b + c + d = target? Find all unique quadruplets in the array which gives the sum of target.

    Note:
        1. Elements in a quadruplet (a,b,c,d) must be in non-descending order. (ie, a ≤ b ≤ c ≤ d)
        2. The solution set must not contain duplicate quadruplets.</p>

<p><b>Example :</b>
<br>

    Given array S = {1 0 -1 0 -2 2}, and target = 0

    A solution set is:
        (-2, -1, 1, 2)
        (-2,  0, 0, 2)
        (-1,  0, 0, 1)
</p>
<p>
Also make sure that the solution set is lexicographically sorted.
Solution[i] < Solution[j] iff Solution[i][0] < Solution[j][0] OR (Solution[i][0] == Solution[j][0] AND ... Solution[i][k] < Solution[j][k])
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return a list of list of integers
    def fourSum(self, A, B):
        seen = dict()
        
        A.sort()
        
        result = set()
        
        for i in range(len(A)):
            for j in range(i+1, len(A)):
                curr_sum = A[i] + A[j]
                diff = B - curr_sum
                if diff in seen:
                    for prev_sum in seen[diff]:
                        if A[prev_sum[1]] <= A[i] and i > prev_sum[1]:
                            result.add((A[prev_sum[0]], A[prev_sum[1]], A[i], A[j]))
                
                if curr_sum in seen:
                    seen[curr_sum].append((i, j))
                else:
                    seen[curr_sum] = [(i, j)]
        
        return sorted([list(item) for item in result])
```