<h1>Longest Substring Without Repeat</h1>

<p>
Given a string,
find the length of the longest substring without repeating characters.

Example:

The longest substring without repeating letters for "abcabcbb" is "abc", which the length is 3.

For "bbbbb" the longest substring is "b", with the length of 1.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return an integer
    def lengthOfLongestSubstring(self, A):
        n = len(A)
        h = {}
        c=0
        ans = 0
        i=j=0
        while j<n:
            if A[j] in h:
                j = h[A[j]] + 1
                ans = max(c,ans)
                c = 0
                h = {}
            else:
                h[A[j]] = j
                j+=1
                c+=1
        ans = max(c,ans)
        return ans
```