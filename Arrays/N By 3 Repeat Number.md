<h1>N By 3 Repeat Number</h1>

<p>You’re given a read only array of n integers. Find out if any integer occurs more than n/3 times in the array in linear time and constant additional space.
If so, return the integer. If not, return -1.
If there are multiple solutions, return any one.</p>

<p>
<b>Example :</b>

    Input : [1 2 3 1 1]
    Output : 1 
    1 occurs 3 times which is more than 5/3 times. 
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @return an integer
    def repeatedNumber(self, A):
        n = len(A)
        if n == 0:
            return -1
        x,y = 2**31,2**31    
        count_x = 0
        count_y = 0
        
        for i in range(n):
            if x == A[i]:
                count_x+=1
            elif y == A[i]:
                count_y+=1
            elif count_x == 0:
                count_x = 1
                x = A[i]
            elif count_y == 0:
                count_y = 1
                y = A[i]
            else:
                count_y-=1
                count_x-=1
                
        
        count_x,count_y = 0,0
        
        for i in range(n):
            if A[i] == x:
                count_x+=1
            elif A[i] == y:
                count_y +=1
            
        if count_x>=n//3:
            return x
        elif count_y>=n//3:
            return y
        return -1
```