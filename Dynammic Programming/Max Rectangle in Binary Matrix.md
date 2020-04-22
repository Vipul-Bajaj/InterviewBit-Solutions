<h1>Max Rectangle in Binary Matrix</h1>

<p>
Given a 2D binary matrix filled with 0’s and 1’s, find the largest rectangle containing all ones and return its area.

Bonus if you can solve it in O(n^2) or less.

Examples:

    A : 
    [  
        1 1 1
        0 1 1
        1 0 0 
    ]

    Output : 4 

    As the max area rectangle is created by the 2x2 rectangle created by (0,1), (0,2), (1,1) and (1,2)

<h2>Solution</h2>

***

```python
def maxHist(A,n):
    st = []
    max_area = -2**31
    i=0
    while i<n:
        while st and A[st[-1]]>A[i]:
            x = st.pop(-1)
            if st:
                max_area = max(max_area,A[x]*(i-st[-1]-1))
            else:
                max_area = max(max_area,A[x]*i)
        st.append(i)
        i+=1
        
    while st:
        x = st.pop(-1)
        if st:
            max_area = max(max_area,A[x]*(i-st[-1]-1))
        else:
            max_area = max(max_area,A[x]*i)
    return max_area 
class Solution:
    # @param A : list of list of integers
    # @return an integer
    def maximalRectangle(self, A):
        m = len(A)
        if m<0:
            return 0
            
        n = len(A[0])
        
        result = maxHist(A[0],n)  
     
        for i in range(1, m): 
            for j in range(n): 
    
                if (A[i][j] ==1): 
                    A[i][j] += A[i - 1][j]  
    
            result = max(result, maxHist(A[i],n))  
          
        return result  
```