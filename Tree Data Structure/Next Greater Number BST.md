<h1>Next Greater Number BST</h1>

<p>
Given a BST node, return the node which has value just greater than the given node.

Example:

Given the tree

               100
              /   \
            98    102
           /  \
         96    99
          \
           97
Given 97, you should return the node corresponding to 98 as thats the value just greater than 97 in the tree.
If there are no successor in the tree ( the value is the largest in the tree, return NULL).

Using recursion is not allowed.

Assume that the value is always present in the tree.
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
    # @param B : integer
    # @return the root node in the tree
    def getSuccessor(self, A, B):
        inord = []
        
        q = []
        curr = A
        while curr or q:
            if curr:
                q.append(curr)
                curr= curr.left
            else:
                curr= q.pop(-1)
                inord.append(curr)
                curr = curr.right
                
        for i in range(len(inord)):
            if inord[i].val == B:
                return inord[i+1] if i+1<len(inord) else None
                
        return None
```