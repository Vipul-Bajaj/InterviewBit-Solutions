<h1>Largest Number</h1>

<p>
Given a list of non negative integers, arrange them such that they form the largest number.

For example:

Given [3, 30, 34, 5, 9], the largest formed number is 9534330.

Note: The result may be very large, so you need to return a string instead of an integer.
</p>

<h2>Solution</h2>

***

```python
def compare(x,y):
    xy = int(str(x)+str(y))
    yx = int(str(y)+str(x))
    return ((yx>xy)-(yx<xy))
    
def cmp_to_key(mycomp):
    
    class K:
        
        def __init__(self,obj,*args):
            self.obj = obj
        def __lt__(self,others):
            return mycomp(self.obj,others.obj) < 0
        def __gt__(self,others):
            return mycomp(self.obj,others.obj) > 0
        def __eq__(self,others):
            return mycomp(self.obj,others.obj) == 0
        def __ne__(self,others):
            return mycomp(self.obj,others.obj) != 0
        def __le__(self,others):
            return mycomp(self.obj,others.obj) <= 0
        def __ge__(self,others):
            return mycomp(self.obj,others.obj) >= 0
            
    return K

class Solution:
    # @param A : tuple of integers
    # @return a strings
    def largestNumber(self, A):
        A=sorted(A,key=cmp_to_key(compare))
        A = list(map(str,A))
        num = "".join(A)
        num = int(num)
        return str(num)
```