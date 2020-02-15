<h1>Sliding Window Maximum</h1>

<p>
Given an array of integers A. There is a sliding window of size B which
is moving from the very left of the array to the very right.
You can only see the w numbers in the window. Each time the sliding window moves
rightwards by one position. You have to find the maximum for each window.
The following example will give you more clarity.

The array A is [1 3 -1 -3 5 3 6 7], and B is 3.

|   Window position   | Max |
| :-----------------: | :-: |
| [1 3 -1] -3 5 3 6 7 |  3  |
| 1 [3 -1 -3] 5 3 6 7 |  3  |
| 1 3 [-1 -3 5] 3 6 7 |  5  |
| 1 3 -1 [-3 5 3] 6 7 |  5  |
| 1 3 -1 -3 [5 3 6] 7 |  6  |
| 1 3 -1 -3 5 [3 6 7] |  7  |

Return an array C, where C[i] is the maximum value of from A[i] to A[i+B-1].
Note: If B > length of the array, return 1 element with the max of the array.
</p>

<p><b>Example :</b>
<br>

```python
Input 1:
    A = [1, 3, -1, -3, 5, 3, 6, 7]
    B = 3
Output 1:
    C = [3, 3, 5, 5, 6, 7]
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @param B : integer
    # @return a list of integers
    def slidingMaximum(self, A, B):
        n = len(A)
        Qi = []
        max_st = []
        for i in range(B): 
        	
        	while Qi and A[i] >= A[Qi[-1]] : 
        		Qi.pop() 
        	
        	Qi.append(i); 
        	
        for i in range(B, n): 
        	
        	max_st.append(A[Qi[0]])
        	while Qi and Qi[0] <= i-B: 
        		
        		Qi.pop(0) 
        
        	while Qi and A[i] >= A[Qi[-1]] : 
        		Qi.pop(-1) 
        	
        	Qi.append(i) 
        
        max_st.append(A[Qi[0]])
        
        return max_st
```