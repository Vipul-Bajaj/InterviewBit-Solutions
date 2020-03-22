<h1>Root to Leaf Paths With Sum</h1>

<p>
Given a binary tree and a sum, find all root-to-leaf paths where each path’s sum equals the given sum.

For example:
Given the below binary tree and sum = 22,

              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1
return 

    [
        [5,4,11,2],
        [5,8,4,5]
    ]
</p>

<h2>Solution</h2>

***

```python
# Definition for a  binary tree node
# class TreeNode:
#    def __init__(self, x):
#        self.val = x
#        self.left = None
#        self.right = None
def pathSum(node,s,res,path):
    if node and node.left is None and node.right is None and s-node.val == 0:
        path += [node.val]
        res.append(path.copy())
        path.pop(-1)
        return 
    if node is None:
        return
        
    pathSum(node.left,s-node.val,res,path + [node.val])
    pathSum(node.right,s-node.val,res,path + [node.val])
    
    return
class Solution:
    # @param A : root node of tree
    # @param B : integer
    # @return a list of list of integers
    def pathSum(self, A, B):
        res = []
        pathSum(A,B,res,[])
        return res
```