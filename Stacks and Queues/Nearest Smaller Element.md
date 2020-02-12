<h1>Nearest Smaller Element</h1>

<p>
Given an array, find the nearest smaller element G[i] for every element A[i] in the array such that the element has an index smaller than i.

More formally,

    G[i] for an element A[i] = an element A[j] such that 
    j is maximum possible AND 
    j < i AND
    A[j] < A[i]
Elements for which no smaller element exist, consider next smaller element as -1.

<p><b>Example :</b>
<br>

```python
Input 1:
    A = [4, 5, 2, 10, 8]
Output 1:
    G = [-1, 4, -1, 2, 2]
Explaination 1:
    index 1: No element less than 4 in left of 4, G[1] = -1
    index 2: A[1] is only element less than A[2], G[2] = A[1]
    index 3: No element less than 2 in left of 2, G[3] = -1
    index 4: A[3] is nearest element which is less than A[4], G[4] = A[3]
    index 4: A[3] is nearest element which is less than A[5], G[5] = A[3]
    
Input 2:
    A = [3, 2, 1]
Output 2:
    [-1, -1, -1]
Explaination 2:
    index 1: No element less than 3 in left of 3, G[1] = -1
    index 2: No element less than 2 in left of 2, G[2] = -1
    index 3: No element less than 1 in left of 1, G[3] = -1
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return a list of integers
    def prevSmaller(self, A):
        st = []
        ans = [-1]
        
        n = len(A)
        
        for i in range(1,n):
            if A[i-1]<A[i]:
                st.append(A[i-1])
                ans.append(A[i-1])
            else:
                while st and st[-1]>=A[i]:
                    st.pop(-1)
                if st:
                    ans.append(st[-1])
                    st.append(A[i])
                else:
                    ans.append(-1)
        return ans
```