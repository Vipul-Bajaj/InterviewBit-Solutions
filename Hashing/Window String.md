<h1>Window String</h1>

<p>
Given a string S and a string T, find the minimum window in S which will contain all the characters in T in linear time complexity.
Note that when the count of a character C in T is N, then the count of C in minimum window in S should be at least N.

<b>Example :</b>

    S = "ADOBECODEBANC"
    T = "ABC"

Minimum window is "BANC"

    Note:
        1. If there is no such window in S that covers all characters in T, return the empty string ''.
        2. If there are multiple such windows, return the first occurring minimum window ( with minimum start index ).
</p>

<h2>Solution</h2>

***

```python
from collections import defaultdict, Counter
class Solution:
    # @param A : string
    # @param B : string
    # @return a strings
    def minWindow(self, A, B):
        S,T = A,B
        if len(T) > len(S): return ""
        tCounter = Counter(T)
        sPos = defaultdict(list)
        n, m = len(S), len(T)
        minlen, startP = n+1, -1
        output = ""
        for i in range(n):
            if tCounter[S[i]] >= 1:
                tCounter[S[i]] -= 1
                m -= 1
                sPos[S[i]].append(i)
                if startP < 0:
                    startP = i
            elif sPos[S[i]] == []: continue
            else:
                pos = sPos[S[i]].pop(0)
                sPos[S[i]].append(i)
                if pos > startP: continue
            #m > 0 means there's no such fitting substring yet
            if m > 0: continue
            find_newS = []
            for val in sPos.values():
                if not val: continue
                find_newS.append(val[0])
            startP = min(find_newS)
            if minlen > (i - startP + 1):
                minlen = (i - startP + 1)
                output = S[startP: i+1]
        return output
```