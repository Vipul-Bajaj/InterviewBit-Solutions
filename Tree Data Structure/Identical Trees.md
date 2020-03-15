<h1>Identical Trees</h1>

<p>
Given two binary trees, write a function to check if they are equal or not.

Two binary trees are considered equal if they are structurally identical and the nodes have the same value.

Return 0 / 1 ( 0 for false, 1 for true ) for this problem

<b>Example :</b>

    Input : 

        1       1
       / \     / \
      2   3   2   3

    Output : 
    1 or True
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
def checkIdentical(tree_a,tree_b):
    if tree_a is None and tree_b is None:
        return 1
    if tree_a and tree_b and tree_a.val != tree_b.val:
        return 0
    if (tree_a and tree_b is None) or (tree_b and tree_a is None):
        return 0
        
    return checkIdentical(tree_a.left,tree_b.left) and checkIdentical(tree_a.right,tree_b.right)
class Solution:
    # @param A : root node of tree
    # @param B : root node of tree
    # @return an integer
    def isSameTree(self, A, B):
        return checkIdentical(A,B)
```