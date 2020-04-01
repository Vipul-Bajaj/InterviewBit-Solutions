<h1>Recover Binary Search Tree</h1>

<p>
Two elements of a binary search tree (BST) are swapped by mistake.
Tell us the 2 values swapping which the tree will be restored.

Note:
    A solution using O(n) space is pretty straight forward. Could you devise a constant space solution? 
Example :

    Input : 
         1
        / \
       2   3

    Output : 
       [1, 2]

    Explanation : Swapping 1 and 2 will change the BST to be 
            2
            / \
        1   3
    which is a valid BST     
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
def correct(root,prev,first,middle,last):
    if root:
        correct(root.left,prev,first,middle,last)
        if prev[0] and root.val<prev[0].val:
            if first[0] == None:
                first[0] = prev[0]
                middle[0] = root
            else:
                last[0]=root
            
        prev[0]=root
        correct(root.right,prev,first,middle,last)
class Solution:
    # @param A : root node of tree
    # @return a list of integers
    def recoverTree(self, A):
        prev = [None]
        first = [None]
        middle = [None]
        last = [None]
        correct(A,prev,first,middle,last)

        if first[0] and last[0]:
            return sorted([first[0].val,last[0].val])
        elif first[0] and middle[0]:
            return sorted([first[0].val,middle[0].val])
```