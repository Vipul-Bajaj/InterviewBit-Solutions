<h1>Stepping Numbers</h1>

<p>
Given N and M find all stepping numbers in range N to M

The stepping number:

    A number is called as a stepping number if the adjacent digits have a difference of 1.
    e.g 123 is stepping number, but 358 is not a stepping number

Example:

    N = 10, M = 20
    all stepping numbers are 10 , 12 

Return the numbers in sorted order.

<h2>Solution</h2>

***

```python
def bfs(n,m,num,ans):
    q = []
    q.append(num)
    
    while q:
        
        stepnum = q.pop(0)
        
        if n<=stepnum<=m:
            ans.append(stepnum)
            
        if stepnum == 0 or stepnum > m:
            continue
        
        last_digit = stepnum % 10
        
        left_neighbour = stepnum*10 + (last_digit-1)
        right_neighbour = stepnum*10 + (last_digit+1)
        
        if last_digit == 0:
            q.append(right_neighbour)
        elif last_digit == 9:
            q.append(left_neighbour)
        else:
            q.append(left_neighbour)
            q.append(right_neighbour)
class Solution:
    # @param A : integer
    # @param B : integer
    # @return a list of integers
    def stepnum(self, A, B):
        res = []
        for i in range(10):
            bfs(A,B,i,res)
            
        return sorted(res)
```