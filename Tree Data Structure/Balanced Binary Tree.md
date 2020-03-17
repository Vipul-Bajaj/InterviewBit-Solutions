<h1>Balanced Binary Tree</h1>

<p>
Given a binary tree, determine if it is height-balanced.

    Height-balanced binary tree : is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1. 

Return 0 / 1 ( 0 for false, 1 for true ) for this problem

Example :

    Input : 
              1
             / \
            2   3

    Return : True or 1 

    Input 2 : 
             3
            /
           2
          /
         1

    Return : False or 0 
             Because for the root node, left subtree has depth 2 and right subtree has depth 0. 
             Difference = 2 > 1. 
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
def getHeight(node):
    if node is None:
        return 0
    
    return max(getHeight(node.left),getHeight(node.right))+1
    
def checkBalance(node):
    if node is None:
        return True
        
    lh = getHeight(node.left)
    rh = getHeight(node.right)
    
    if abs(lh-rh)<=1 and checkBalance(node.left) and checkBalance(node.right):
        return True
    else:
        return False
class Solution:
    # @param A : root node of tree
    # @return an integer
    def isBalanced(self, A):
        if checkBalance(A):
            return 1
        return 0    
```