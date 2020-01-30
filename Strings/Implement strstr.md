<h1>Implement strstr</h1>

<p>Implement strstr() (KMP Algo)

```python
strstr - locate a substring ( needle ) in a string ( haystack ). 
```

<b>NOTE: Good clarification questions:</b>

```python
1. What should be the return value if the needle is empty?
2. What if both haystack and needle are empty?
For the purpose of this problem, assume that the return value should be -1 in both cases.
```

Returns the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

<b>Warning : DO NOT USE LIBRARY FUNCTION FOR ATOI.</b><br>
If you do, we will disqualify your submission retroactively and give you penalty points.

</p>
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : string
    # @return an integer
    def strStr(self, A, B):
        # A is haystack
        # B is needle
        
        N = len(A)
        M = len(B)
        if B=='' or (A=='' and B==''):
            return -1
        
        l = 0
        lps = [0]*M 
        lps[0]
        i = 1
      
        while i < M: 
            if B[i]== B[l]: 
                l += 1
                lps[i] = l
                i += 1
            else: 
                if l != 0: 
                    l = lps[l-1] 
                else: 
                    lps[i] = 0
                    i += 1
                    
        
        j=0
        i = 0
        while i < N: 
            if B[j] == A[i]: 
                i += 1
                j += 1
      
            if j == M: 
                return i-j
      
            elif i < N and B[j] != A[i]: 
                if j != 0: 
                    j = lps[j-1] 
                else: 
                    i += 1
                    
        return -1
```