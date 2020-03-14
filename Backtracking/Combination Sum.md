<h1>Combination Sum</h1>

<p>
Given a set of candidate numbers (C) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

The same repeated number may be chosen from C unlimited number of times.

    Note:
    1. All numbers (including target) will be positive integers.
    2. Elements in a combination (a1, a2, … , ak) must be in non-descending order. (ie, a1 ≤ a2 ≤ … ≤ ak).
    3. The combinations themselves must be sorted in ascending order.
    4. CombinationA > CombinationB iff (a1 > b1) OR (a1 = b1 AND a2 > b2) OR … (a1 = b1 AND a2 = b2 AND … ai = bi AND ai+1 > bi+1)
    5. The solution set must not contain duplicate combinations.

<b>Example,</b>

    Input :
        Given candidate set 2,3,6,7 and target 7,
        A solution set is:
    Output :
        [2, 2, 3]
        [7]
</p>
<p>  

    Warning : DO NOT USE LIBRARY FUNCTION FOR GENERATING COMBINATIONS.
    Example : itertools.combinations in python.
    If you do, we will disqualify your submission retroactively and give you penalty points. 
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return a list of list of integers
    def combinationSum(self, A, B):
        A.sort()
        def generateComb(arr,s,res,r,i):
            if s<0:
                return
            if s == 0:
                if r[::] not in res:
                    res.append(r[::])
                return
            
            while i<len(arr) and s-arr[i]>=0:
                r.append(arr[i])
                generateComb(arr,s-arr[i],res,r,i)
                i+=1
                r.pop(-1)
                
        res = []
        generateComb(A,B,res,[],0)
        
        return sorted(res)
```