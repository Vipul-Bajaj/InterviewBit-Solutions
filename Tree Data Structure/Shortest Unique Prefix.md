<h1>Shortest Unique Prefix</h1>

<p>
Find shortest unique prefix to represent each word in the list.

<b>Example:</b>

    Input: [zebra, dog, duck, dove]
    Output: {z, dog, du, dov}
    where we can see that
    zebra = z
    dog = dog
    duck = du
    dove = dov

NOTE : Assume that no word is prefix of another. In other words, the representation is always possible. 
</p>

<h2>Solution</h2>

***

```python
class Trie:
    def __init__(self):
        self.letters={}
    def addString(self,s):
        letters=self.letters
        for c in s:
            if(c not in letters):
                letters[c]={"freq":1}
            else:
                letters[c]["freq"]+=1
            letters=letters[c]
        letters["*"]=True #marks the end of word
        
    def generateUniquePrefix(self,s):
        prefix=[]
        letters=self.letters
        for c in s:
            prefix.append(c)
            if(letters[c]["freq"]==1):
                break
            letters=letters[c]
            
        return "".join(prefix)
class Solution:
    # @param A : list of strings
    # @return a list of strings
    
    def prefix(self, A):
        t=Trie()
        for s in A:
            t.addString(s)
        ans=[]
        for s in A:
            prefix=t.generateUniquePrefix(s)
            ans.append(prefix)
        return ans
```