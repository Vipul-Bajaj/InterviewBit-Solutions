<h1>Kth Smallest Element In Tree</h1>

<p>
Given a binary search tree, write a function to find the kth smallest element in the tree.

NOTE : You may assume 1 <= k <= Total number of nodes in BST 

Example :

    Input : 
          2
         / \
        1   3

    and k = 2

    Return : 2

    As 2 is the second smallest element in the tree.
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
    # @return an integer
    def kthsmallest(self, A, B):
        inord = []
        curr = A
        while inord or curr:
            if curr:
                inord.append(curr)
                curr = curr.left
            else:
                curr = inord.pop()
                B-=1
                if B==0:
                    return curr.val
                curr = curr.right
                
        return None   
```