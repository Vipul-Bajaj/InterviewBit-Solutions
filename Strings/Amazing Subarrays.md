<h1>Amazing Subarrays</h1>

<p>You are given a string S, and you have to find all the amazing substrings of S.

Amazing Substring is one that starts with a vowel (a, e, i, o, u, A, E, I, O, U).
</p>

<p>
<b>Input :</b>
<br>

```python
Only argument given is string S.
```
<b>Output :</b>
<br>

```python
Return a single integer X mod 10003, here X is number of Amazing Substrings in given string.
```

<b>Constraints :</b>
<br>

```python
1 <= length(S) <= 1e6
S can have special characters
```

<b>Example :</b>
<br>

```python
Input
    ABEC

Output
    6

Explanation
    Amazing substrings of given string are :
    1. A
    2. AB
    3. ABE
    4. ABEC
    5. E
    6. EC
    here number of substrings are 6 and 6 % 10003 = 6.
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return an integer
    def solve(self, A):
        vowels = ['A','E','I','O','U']
        n = len(A)
        A = A.upper()
        c = 0
        for i in range(n):
            if A[i] in vowels:
                c+=(n-i)%10003
                
        return c%10003
```