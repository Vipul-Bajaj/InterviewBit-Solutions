<h1>2 Sum</h1>

<p>Given an array of integers, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 < index2. Please note that your returned answers (both index1 and index2 ) are not zero-based.
Put both these numbers in order in an array and return the array from your function ( Looking at the function signature will make things clearer ). Note that, if no pair exists, return empty list.

If multiple solutions exist, output the one where index2 is minimum. If there are multiple solutions with the minimum index2, choose the one with minimum index1 out of them.</p>

<p><b>Example :</b>
<br>

    Input: [2, 7, 11, 15], target=9
    Output: index1 = 1, index2 = 2
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @param B : integer
    # @return a list of integers
    def twoSum(self, A, B):
        idx1 = 2**31
        idx2 = 2**31
        h = {}
        for i in range(len(A)):
            if A[i] in h:
                h[A[i]] += [i]
            else:
                h[A[i]] = [i]
        for i in range(len(A)):
            if B-A[i] in h:
                id1,id2 = min(h[B-A[i]])+1,i+1
                if id2>id1:
                    if id2 < idx2:
                        idx1,idx2 = id1,id2
                    elif id2 == idx2:
                        if id1<idx1:
                            idx1,idx2 = id1,id2
            else:
                h[A[i]] = [i]
                
        if idx1 == idx2 or idx1 == 2**31 or idx2 == 2**31:
            return []
        return [idx1,idx2]
```