<h1>Symmetric Binary Tree</h1>

<p>
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

Example :

         1
        / \
       2   2
      / \ / \
     3  4 4  3
The above binary tree is symmetric.
But the following is not:

         1
        / \
       2   2
        \   \
         3   3
Return 0 / 1 ( 0 for false, 1 for true ) for this problem
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
def inorder(node,inord):
    if node is None:
        return
    
    inorder(node.left,inord)
    inord.append(node.val)
    inorder(node.right,inord)
    
class Solution:
    # @param A : root node of tree
    # @return an integer
    def isSymmetric(self, A):
        left = []
        right = []
        
        inorder(A.left,left)
        inorder(A.right,right)
        
        if left == right[::-1]:
            return 1
        return 0
```