<h1>PreOrder Traversal</h1>

<p>
Given a binary tree, return the preorder traversal of its nodes’ values.

Example :
Given binary tree

    1
      \
        2
      /
    3
return [1,2,3].

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
    def preorderTraversal(self, A):
        res=[]
        st = [A]
        while st:
            node  = st.pop(-1)
            res.append(node.val)
            if node.right:
                st.append(node.right)
            if node.left:
                st.append(node.left)
                
        return res
```