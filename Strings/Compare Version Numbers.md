<h1>Compare Version Numbers</h1>

<p>Compare two version numbers version1 and version2.

```python
If version1 > version2 return 1,
If version1 < version2 return -1,
otherwise return 0.
```

You may assume that the version strings are non-empty and contain only digits and the . character.
The . character does not represent a decimal point and is used to separate number sequences.
For instance, 2.5 is not "two and a half" or "half way to version three", it is the fifth second-level revision of the second first-level revision.

Here is an example of version numbers ordering:

```python
0.1 < 1.1 < 1.2 < 1.13 < 1.13.4
```
</p>
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : string
    # @return an integer
    def compareVersion(self, A, B):
        str_split_A = A.split(".")
        str_split_B = B.split(".")
        
        m,n = len(str_split_A),len(str_split_B)
        
        split_A = []
        split_B = []
        
        for i in range(m):
            if i == m-1 and int(str_split_A[i])==0:
                continue
            split_A.append(int(str_split_A[i]))
        
        
        for i in range(n):
            if i == n-1 and int(str_split_B[i])==0:
                continue
            split_B.append(int(str_split_B[i]))
        
        i,j=0,0
        
        m,n = len(split_A),len(split_B)
        
        while i<m and j<n:
            if split_A[i]>split_B[j]:
                return 1
            elif split_A[i]<split_B[j]:
                return -1
            else:
                i+=1
                j+=1
                
        if i == m and j != n:
            return -1
        elif j == n and i != m:
            return 1
        return 0
```