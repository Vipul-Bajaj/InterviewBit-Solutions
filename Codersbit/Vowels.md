<h1>Vowels</h1>

<p>
You are given an Integer N.

You have to find how many different strings of length N can be made using Vowels (a, e, i, o, u) only and by following given rules :

‘a’ can only be followed by ‘e’ and ‘i’.

‘e’ can only be followed by ‘i’.

‘i’ can only be followed by ‘a’, ‘e’, ‘o’, and ‘u’.

‘o’ can only be followed by ‘a’ and ‘u’.

‘u’ can only be followed by ‘o’ and ‘e’.

for example N = 2

    strings starting with 'a' of length 2 are:
        1. "ae"
        2. "ai"
    strings starting with 'e' of length 2 are:
        1. "ei"
    strings starting with 'i' of length 2 are:
        1. "ia"
        2. "io"
        3. "iu"
        4. "ie"
    strings starting with 'o' of length 2 are:
        1. "oa"
        2. "ou"
    strings starting with 'u' of length 2 are:
        1. "uo"
        2. "ue"

    so total number of strings can be made using vowels and following above rules will be 11.

Input Format

    Given the only argument N of type Integer.
Output Format

    Return a single Integer X mod (1e9 + 7), i.e number of Strings that can be made using vowels and following above rules.
Constraints

    1 <= N <= 1e5
    strings will have only lowercase letters.
Example

    Example Input:
    N = 1
        
    Example Output:
        5

    Explanation:
        Strings of length 1 are :
        1. "a"
        2. "e"
        3. "i"
        4. "o"
        5. "u"

    Example Input:
    N = 2
        
    Example Output:
        11

    Explanation:
        as explained above.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return an integer
    def solve(self, A):
        if A == 0:
            return 0
            
        a,e,i,o,u = 1,1,1,1,1
        for k in range(2,A+1):
            new_a = e + i
            new_e = i
            new_i = a + e + o + u
            new_o = a + u
            new_u = e + o
            a,e,i,o,u = new_a,new_e,new_i,new_o,new_u
        return (a+e+i+o+u)%1000000007
```