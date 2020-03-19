<h1>Construct Binary Tree From Inorder And Preorder</h1>

<p>
Given preorder and inorder traversal of a tree, construct the binary tree.

    Note: You may assume that duplicates do not exist in the tree. 

Example :

    Input :
        Preorder : [1, 2, 3]
        Inorder  : [2, 1, 3]

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
        if start> end:
            return
        
        node = TreeNode(postord[self.idx])
        ind = hm[node.val]
        self.idx+=1
        if start == end:
            return node
        
        node.left = self.buildBinaryTree(inord,postord,start,ind-1,hm)
        node.right = self.buildBinaryTree(inord,postord,ind+1,end,hm)
        return node
    def buildTree(self, A, B):
        self.idx = 0
        hm = {}
        for i in range(len(B)):
            hm[B[i]] = i
            
        return self.buildBinaryTree(B,A,0,len(B)-1,hm)
```