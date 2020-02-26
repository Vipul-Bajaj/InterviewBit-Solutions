<h1>Anagrams</h1>

<p>
Given an array of strings, return all groups of strings that are anagrams. Represent a group by a list of integers representing the index in the original list. Look at the sample case for clarification.

    Anagram : a word, phrase, or name formed by rearranging the letters of another, such as 'spar', formed from 'rasp' 
 
    Note: All inputs will be in lower-case.
</p>

<p><b>Example :</b>
<br>

    Input : cat dog god tca
    Output : [[1, 4], [2, 3]]
</p>
<p>
cat and tca are anagrams which correspond to index 1 and 4.
dog and god are another set of anagrams which correspond to index 2 and 3.
The indices are 1 based ( the first element has index 1 instead of index 0).

    Ordering of the result : You should not change the relative ordering of the words / phrases within the group. Within a group containing A[i] and A[j], A[i] comes before A[j] if i < j.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of strings
    # @return a list of list of integers
    def anagrams(self, A):
        h = {}
        for i,word in enumerate(A):
            ch = sorted(list(word))
            ch = ''.join(ch)
            if ch in h:
                h[ch].append(i+1)
            else:
                h[ch] = [i+1]
            
        h = h.values()
        h = list(h)
        h.sort()
        return h
```