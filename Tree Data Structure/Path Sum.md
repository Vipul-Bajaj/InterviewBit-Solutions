<h1>Path Sum</h1>

<p>
Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

Example :

Given the below binary tree and sum = 22,

              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1
return true, as there exist a root-to-leaf path 5->4->11->2 which sum is 22.

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
def pathSum(node,s):
    if node and node.left is None and node.right is None and s-node.val == 0:
        return 1
    if node is None:
        return 0
        
    left=right=0
    left = pathSum(node.left,s-node.val) or left
    right = pathSum(node.right,s-node.val) or right
    
    return left or right    
class Solution:
    # @param A : root node of tree
    # @param B : integer
    # @return an integer
    def hasPathSum(self, A, B):
        
        return pathSum(A,B)          
```