<h1>Find Permutation</h1>

<p>
Given a positive integer n and a string s consisting only of letters D or I, you have to find any permutation of first n positive integer that satisfy the given input string.

D means the next number is smaller, while I means the next number is greater.

Notes

    1. Length of given string s will always equal to n - 1
    2. Your solution should run in linear time and space.
</p>

<p>
<b>Example :</b>
<br>

    Input 1:
        n = 3
        s = ID

    Return: 
        [1, 3, 2]
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : integer
    # @return a list of integers
    def findPerm(self, A, B):
        h,l=B,1
        res = []
        for i in A:
            if i=="D":
                res.append(h)
                h-=1
            else:
                res.append(l)
                l+=1
        res.append(l) 
        return res
```