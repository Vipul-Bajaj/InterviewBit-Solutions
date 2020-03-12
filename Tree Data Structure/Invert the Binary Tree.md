<h1>Invert the Binary Tree</h1>

<p>
Given a binary tree, invert the binary tree and return it.
Look at the example for more details.

Example :
Given binary tree

          1
        /   \
       2     3
      / \   / \
     4   5 6   7
invert and return

          1
        /   \
       3     2
      / \   / \
     7   6 5   4
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
    # @return the root node in the tree
    def invertTree(self, A):
        if A is None:
            return A
        if A.left and A.right:
            A.left,A.right = A.right,A.left
        elif A.left:
            A.right = A.left
            A.left = None
        elif A.right:
            A.left = A.right
            A.right = None
        self.invertTree(A.left)
        self.invertTree(A.right)
        
        return A
```