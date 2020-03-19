<h1>Binary Tree From Inorder And Postorder</h1>

<p>
Given inorder and postorder traversal of a tree, construct the binary tree.

    Note: You may assume that duplicates do not exist in the tree. 

Example :

    Input : 
        Inorder : [2, 1, 3]
        Postorder : [2, 3, 1]

    Return : 
            1
           / \
          2   3

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
    # @param A : list of integers
    # @param B : list of integers
    # @return the root node in the tree
    idx = 0
    def buildBinaryTree(self,inord,postord,start,end,hm):
        if len(postord) == 0 or start> end:
            return
        
        node = TreeNode(postord[self.idx])
        ind = hm[node.val]
        self.idx-=1
        if start == end:
            return node
        
        node.right = self.buildBinaryTree(inord,postord,ind+1,end,hm)
        node.left = self.buildBinaryTree(inord,postord,start,ind-1,hm)
        return node
    def buildTree(self, A, B):
        self.idx = len(B)-1
        hm = {}
        for i in range(len(A)):
            hm[A[i]] = i
            
        return self.buildBinaryTree(A,B,0,len(A)-1,hm)
```