<h1>Rain Water Trapped</h1>

<p>Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.
</p>

<p><b>Example :</b>
<br>
Input 1:

    A = [0,1,0,2,1,0,1,3,2,1,2,1]
Output 1:

    6
Explaination 1: 
<p>
<img src="http://i.imgur.com/0qkUFco.png">
In this case, 6 units of rain water (blue section) are being trapped.
</p>
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @return an integer
    def trap(self, A):
        n = len(A)
    
        result = 0
           
        # maximum element on left and right 
        left_max = 0
        right_max = 0
           
        # indices to traverse the array 
        lo = 0
        hi = n-1
           
        while(lo <= hi):  
          
            if(A[lo] < A[hi]): 
              
                if(A[lo] > left_max): 
      
                    # update max in left 
                    left_max = A[lo] 
                else: 
      
                    # water on curr element = max - curr 
                    result += left_max - A[lo] 
                lo+= 1
              
            else: 
              
                if(A[hi] > right_max): 
                    # update right maximum 
                    right_max = A[hi] 
                else: 
                    result += right_max - A[hi] 
                hi-= 1
              
        return result 
```