<h1>Count and Say</h1>

<p>The count-and-say sequence is the sequence of integers beginning as follows:

```python
1, 11, 21, 1211, 111221, ...
```

1 is read off as one 1 or 11.
11 is read off as two 1s or 21.

21 is read off as one 2, then one 1 or 1211.

Given an integer n, generate the nth sequence.

Note: The sequence of integers will be represented as a string.

</p>

<p><b>Example :</b><br>n = 2<br>the sequence is 11</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return a strings
    def countAndSay(self, A):
        n = A
        f = '1'
        s = '11'
        
        if n == 1:
            return f
        elif n == 2:
            return s
            
        for i in range(3,n+1):
            res = ""
            c = 0
            ele = s[0]
            j = 0
            l = len(s)
            while j<l:
                if ele == s[j]:
                    c+=1
                else:
                    res += str(c) + ele
                    ele = s[j]
                    c = 1
                j+=1
            res += str(c) + ele    
            s = res
        
        return s
```