<h1>Inorder Traversal of Cartesian Tree</h1>

<p>
Given an inorder traversal of a cartesian tree, construct the tree.

    Cartesian tree : is a heap ordered binary tree, where the root is greater than all the elements in the subtree. 
    Note: You may assume that duplicates do not exist in the tree. 

<b>Example :</b>

    Input : [1 2 3]

    Return :   
           3
          /
         2
        /
       1
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
def buildCartTree(A):
    if len(A)==0:
        return None
    
    max_ele = max(A)
    max_ele_idx = A.index(max_ele)
    root = TreeNode(max_ele)
    root.left = buildCartTree(A[0:max_ele_idx])
    root.right = buildCartTree(A[max_ele_idx+1:])
    return root
class Solution:
    # @param A : list of integers
    # @return the root node in the tree
    def buildTree(self, A):
        return buildCartTree(A)
```