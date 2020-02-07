<h1>Longest Palindromic Substring</h1>

<p>Given a string S, find the longest palindromic substring in S.

Substring of string S:

S[i...j] where 0 <= i <= j < len(S)

Palindrome string:

A string which reads the same backwards. More formally, S is palindrome if reverse(S) = S.

Incase of conflict, return the substring which occurs first ( with the least starting index ).
</p>

<b>For Example</b>

```python
Input : "aaaabaaa"
Output : "aaabaaa"
```
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return a strings
    def longestPalindrome(self, A):
        n = len(A)
        if n<2:
            return A
        start = 0
        len_lps = 0
        for i in range(1,n):
            j=i-1
            k=i
            while j>=0 and k<n and A[j]==A[k]:
                if k - j + 1 > len_lps: 
                    start = j 
                    len_lps = k - j + 1
                j -= 1
                k += 1
                
            j = i - 1
            k = i + 1
            while j >= 0 and k < n and A[j] == A[k]: 
                if k - j + 1 > len_lps: 
                    start = j 
                    len_lps = k - j + 1
                j -= 1
                k += 1
                    
        return A[start:start+len_lps]

```