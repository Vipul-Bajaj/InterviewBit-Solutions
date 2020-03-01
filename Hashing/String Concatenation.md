<h1>String Concatenation</h1>

<p>
You are given a string, S, and a list of words, L, that are all of the same length.

Find all starting indices of substring(s) in S that is a concatenation of each word in L exactly once and without any intervening characters.

<b>Example :</b>

    S: "barfoothefoobarman"
    L: ["foo", "bar"]

You should return the indices: [0,9].
(order does not matter).
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : tuple of strings
    # @return a list of integers
    def findSubstring(self, A, B):
        ans = []
        b_hash = 0
        l = len(A)
        m,n = len(B),len(B[0])
        for word in B:
            b_hash+=hash(word)
        
        i=0
        while i<l:
            a = A[i:m*n+i]
            a_hash = 0
            for j in range(0,len(a),n):
                w = a[j:j+n]
                a_hash += hash(w)
            
            if a_hash == b_hash:
                ans.append(i)
            
            i+=1
        
        return ans
```