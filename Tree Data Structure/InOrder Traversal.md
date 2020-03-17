<h1>InOrder Traversal</h1>

<p>
Given a binary tree, return the inorder traversal of its nodes’ values.

Example :

Given binary tree

    1
      \
        2
      /
    3
return [1,3,2].

Using recursion is not allowed.
</p>

<h2>Solution</h2>

***

```python
# Definition for a  binary tree node
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    # @param A : root node of tree
    # @return a list of integers
    def inorderTraversal(self, A):
        curr = A
        st = []
        res = []
        while True:
            if curr:
                st.append(curr)
                curr=curr.left
            
            elif st:
                curr = st.pop()
                res.append(curr.val)
                curr=curr.right
                
            else:
                break
                
        return res
```