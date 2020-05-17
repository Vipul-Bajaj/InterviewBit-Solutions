<h1>Smallest Multiple With 0 and 1</h1>

<p>
You are given an integer N. You have to find smallest multiple of N which consists of digits 0 and 1 only. Since this multiple could be large, return it in form of a string.

Note:

    Returned string should not contain leading zeroes.
For example,

    For N = 55, 110 is smallest multiple consisting of digits 0 and 1.
    For N = 2, 10 is the answer.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return a strings
    def multiple(self, A):
        if A == 1:
            return "1"
        p = [-1]*A
        s = [-1]*A
        steps = [0,1]
        q = [1]
        
        while q:
            curr = q.pop(0)
            if curr == 0:
                break
            for step in steps:
                next_num = (curr*10+step)%A
                if p[next_num]==-1:
                    p[next_num]=curr
                    s[next_num]=step
                    q.append(next_num)
        
        number = ''
        it = 0
        while it!=1:
            number+=str(s[it])
            it = p[it]
        number+='1'
        return number[::-1]
```