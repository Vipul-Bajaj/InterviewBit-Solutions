<h1>Max Depth of Binary Tree</h1>

<p>
Given a binary tree, find its maximum depth.

The maximum depth of a binary tree is the number of nodes along the longest path from the root node down to the farthest leaf node.

    NOTE : The path has to end on a leaf node. 

<b>Example :</b>

         1
        /
       2
max depth = 2.
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

def calcMaxDepth(node,depth):
    if node is None:
        return -2**31-1
    if node and node.left is None and node.right is None:
        return depth
        
    left = calcMaxDepth(node.left,depth+1)
    right = calcMaxDepth(node.right,depth+1)
    return max(left,right)
    
class Solution:
    # @param A : root node of tree
    # @return an integer
    def maxDepth(self, A):
        return calcMaxDepth(A,1)
```