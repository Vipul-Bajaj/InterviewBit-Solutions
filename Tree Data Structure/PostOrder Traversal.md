<h1>PostOrder Traversal</h1>

<p>
Given a binary tree, return the postorder traversal of its nodes’ values.

Example :

Given binary tree

    1
      \
        2
      /
    3
return [3,2,1].

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
    def postorderTraversal(self, A):
        s1 = [A]
        s2 = []
        res = []
        
        while s1:
            node=s1.pop(-1)
            s2.append(node)
            if node.left:
                s1.append(node.left)
            if node.right:
                s1.append(node.right)
                
        while s2:
            node = s2.pop(-1)
            res.append(node.val)
            
        return res
```