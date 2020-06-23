<h1>Longest Subarray Difference</h1>

<p>
You are given an array A of N integers and an integer B.

You have to find the longest subarray of A such that the difference between the maximum and the minimum element of that subarray is strictly less than B.

Input Format

    The first argument given is an Array A, having N integers.
    The second argument is an integer B.
Output Format

    Return an integer X, i.e size of the longest subarray
Constraints

    1 <= N <= 1e5
    1 <= A[i] <= 1e6
    1 <= B <= 1e6
For Example

    Input:
        A = [1, 2, 4]
        B = 2
    Output:
        2
    
    Explanation:
        only subarray which has a difference of maximum and minimum element strictly less than 2 is:
        [1, 2]
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
    
        max_len = 0
        start=0
        
        window = {}
        for end in range(n):
            if A[end] in window:
                window[A[end]]+=1
            else:
                window[A[end]]=1
                
            minimum = min(list(window.keys()))
            maximum = max(list(window.keys()))
            
            if maximum-minimum < B:
                if max_len < (end-start+1):
                    max_len = end-start+1
            else:
                while start<end:
                    window[A[start]]-=1
                    
                    if window[A[start]] == 0:
                        window.pop(A[start])
                        
                    start += 1
                    
                    minimum = min(list(window.keys()))
                    maximum = max(list(window.keys()))
                    
                    if maximum-minimum < B:
                        break
        return max_len
```