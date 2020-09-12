<h1>Valid BST from Preorder</h1>

<p>
You are given a preorder traversal A, of a Binary Search Tree.

Find if it is a valid preorder traversal of a BST.
Problem Constraints

    1 <= A[i] <= 10^6
    1 <= |A| <= 10^5
Input Format

    First and only argument is an integer array A denoting the pre-order traversal.
Output Format
    
    Return an integer:
    0 : Impossible preorder traversal of a BST
    1 : Possible preorder traversal of a BST
Example:

    Input 1:
        A = [7, 7, 10, 10, 9, 5, 2, 8]
    Output 1:
        1

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def solve(self, A):
        st = []
        root = -2**31

        for i in range(len(A)):
            if root>A[i]:
                return 0
            while st and st[-1]<A[i]:
                root = st.pop()
            st.append(A[i])
        
        return 1
```
