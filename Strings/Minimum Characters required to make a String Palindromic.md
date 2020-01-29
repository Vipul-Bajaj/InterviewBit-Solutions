<h1>Minimum Characters required to make a String Palindromic</h1>

<p>Given an string A. The only operation allowed is to insert characters in the beginning of the string.

Find how many minimum characters are needed to be inserted to make the string a palindrome string.</p>

<p>
<b>For Example :</b>
<br>

```python
Input 1:
    A = "ABC"
Output 1:
    2
    Explanation 1:
        Insert 'B' at beginning, string becomes: "BABC".
        Insert 'C' at beginning, string becomes: "CBABC".

Input 2:
    A = "AACECAAAA"
Output 2:
    2
    Explanation 2:
        Insert 'A' at beginning, string becomes: "AAACECAAAA".
        Insert 'A' at beginning, string becomes: "AAAACECAAAA".
```

</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return an integer
    def solve(self, A):
        n = len(A)
        A = A + "$" + A[::-1]
        lps = [0]*len(A)
        j = 0
        i = 1
    
        while i < len(A): 
            if A[i]== A[j]: 
                j += 1
                lps[i] = j
                i += 1
            else: 
                if j != 0: 
                    j = lps[j-1] 
                else: 
                    lps[i] = 0
                    i += 1 
                    
        return n - lps[-1]
```