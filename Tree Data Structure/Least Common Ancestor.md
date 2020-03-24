<h1>Least Common Ancestor</h1>

<p>
Find the lowest common ancestor in an unordered binary tree given two values in the tree.

    Lowest common ancestor : the lowest common ancestor (LCA) of two nodes v and w in a tree or directed acyclic graph (DAG) is the lowest (i.e. deepest) node that has both v and w as descendants. 
Example :

             _______3______
            /              \
        ___5__           ___1__
       /      \         /      \
      6       _2_      0        8
             /   \
            7     4
For the above tree, the LCA of nodes 5 and 1 is 3.

    LCA = Lowest common ancestor 
Please note that LCA for nodes 5 and 4 is 5.

    1. You are given 2 values. Find the lowest common ancestor of the two nodes represented by val1 and val2
    2. No guarantee that val1 and val2 exist in the tree. If one value doesn’t exist in the tree then return -1.
    3. There are no duplicate values.
    4. You can use extra memory, helper functions, and can modify the node struct but, you can’t add a parent pointer.
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
def findLCA(A,B,C,v):
    if A is None:
        return A
    if A.val == B : 
        v[0] = True
        return A 
  
    if A.val == C: 
        v[1] = True
        return A 
    left = findLCA(A.left,B,C,v)
    right = findLCA(A.right,B,C,v)
    if left and right:
        return A
    if left:
        return left
    else:
        return right
        
def find(root, k): 
      
    # Base Case 
    if root is None: 
        return False
      
    # If key is present at root, or if left subtree or right 
    # subtree , return true 
    if (root.val == k or find(root.left, k) or
        find(root.right, k)): 
        return True
      
    # Else return false 
    return False
    
class Solution:
    # @param A : root node of tree
    # @param B : integer
    # @param C : integer
    # @return an integer
    def lca(self, A, B, C):
        v=[False,False]
        lca = findLCA(A,B,C,v)
        if (v[0] and v[1]) or (v[0] and find(lca, C)) or (v[1] and find(lca, B)): 
            return lca.val
        else:
            return -1
```