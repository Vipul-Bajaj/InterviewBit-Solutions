<h1>Longest Common Prefix</h1>

<p>Given the array of strings A,
you need to find the longest string S which is the prefix of ALL the strings in the array.

Longest common prefix for a pair of strings S1 and S2 is the longest string S which is the prefix of both S1
and S2.

For Example, longest common prefix of "abcdefgh" and "abcefgh" is "abc".
</p>

<b>For Example</b>

```python
Input 1:
    A = ["abcdefgh", "aefghijk", "abcefgh"]
Output 1:
    "a"
    Explanation 1:
        Longest common prefix of all the strings is "a".

Input 2:
    A = ["abab", "ab", "abcd"];
Output 2:
    "ab"
    Explanation 2:
        Longest common prefix of all the strings is "ab".
```
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of strings
    # @return a strings
    def longestCommonPrefix(self, A):
        n = len(A)
    
        s = A[0]
        m = len(s)
        for j in range(m,-1,-1):
            st = s[:j]
            found = True
            for i in range(1,n):
                if st not in A[i]:
                    found = False
                    break
                
            if found == True:
                return st
        return ""
```