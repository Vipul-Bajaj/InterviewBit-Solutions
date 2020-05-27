<h1>Maximum Unsorted Subarray</h1>

<p>You are given an array (zero indexed) of N non-negative integers, A0, A1 ,…, AN-1.
Find the minimum sub array Al, Al+1 ,…, Ar so if we sort(in ascending order) that sub array, then the whole array should get sorted.
If A is already sorted, output -1.

Example :

    Input 1:

    A = [1, 3, 2, 4, 5]

    Return: [1, 2]

    Input 2:

    A = [1, 2, 3, 4, 5]

    Return: [-1]
In the above example(Input 1), if we sort the subarray A1, A2, then whole array A should get sorted.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return a list of integers
    def subUnsort(self, A):
        n = len(A)
        e = n-1
        s = 0
        for s in range(0,n-1): 
            if A[s] > A[s+1]: 
                break
              
        # if s+1 == n-1: 
        #     return [-1]
      
        # step 1(b) of above algo 
        e= n-1
        while e > 0: 
            if A[e] < A[e-1]: 
                break
            e -= 1
      
        # step 2(a) of above algo 
        _max = A[s] 
        _min = A[s] 
        for i in range(s+1,e+1): 
            if A[i] > _max: 
                _max = A[i] 
            if A[i] < _min: 
                _min = A[i] 
                  
        # step 2(b) of above algo 
        for i in range(s): 
            if A[i] > _min: 
                s = i 
                break
      
        # step 2(c) of above algo 
        i = n-1
        while i >= e+1: 
            if A[i] < _max: 
                e = i 
                break
            i -= 1
        
        if s>=e:
            return [-1]
        return [s,e]
```