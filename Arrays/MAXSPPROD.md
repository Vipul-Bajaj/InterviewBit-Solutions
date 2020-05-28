<h1>MAXSPPROD</h1>

<p>You are given an array A containing N integers. The special product of each ith integer in this array is defined as the product of the following:<ul>

1. LeftSpecialValue: For an index i, it is defined as the index j such that A[j]>A[i] (i>j). If multiple A[j]’s are present in multiple positions, the LeftSpecialValue is the maximum value of j.

2. RightSpecialValue: For an index i, it is defined as the index j such that A[j]>A[i] (j>i). If multiple A[j]s are present in multiple positions, the RightSpecialValue is the minimum value of j.

Write a program to find the maximum special product of any integer in the array.

Input: 
    You will receive array of integers as argument to function.

Return: 
    Maximum special product of any integer in the array modulo 1000000007.

Note: If j does not exist, the LeftSpecialValue and RightSpecialValue are considered to be 0.

Constraints 
    1 <= N <= 10^5 1 <= A[i] <= 10^9
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def maxSpecialProduct(self, A):
        n = len(A)
        left,right=[0]*n,[0]*n
        
        st = []
        
        for i in range(n):
            while st and A[i]>=A[st[-1]]:
                st.pop()
                
            left[i] = st[-1] if st else 0
            st.append(i)
            
        st = []
        for i in range(n-1,-1,-1):
            while st and A[i]>=A[st[-1]]:
                st.pop()
                
            right[i] = st[-1] if st else 0
            st.append(i)
            
        max_res = 0
        for i in range(n):
            max_res = max(max_res,left[i]*right[i])
            
        return max_res%1000000007
```