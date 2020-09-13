<h1>Remove Half Nodes</h1>

<p>
Given a binary tree A with N nodes.
You have to remove all the half nodes and return the final binary tree.

NOTE:

    1. Half nodes are nodes which have only one child.
    2. Leaves should not be touched as they have both children as NULL.
Problem Constraints

    1 <= N <= 10^5
Input Format

    First and only argument is an pointer to root of the binary tree A.
Output Format
    
    Return a pointer to the root of the new binary tree.
Example:

    Input 1:
           1
         /   \
        2     3
       / 
      4
    Input 2:
            1
          /   \
         2     3
        / \     \
       4   5     6
    Output 1:
           1
         /    \
        4      3
    Output 2:
            1
          /   \
         2     6
        / \
       4   5
    Explanation 1:
        The only half node present in the tree is 2 so we will remove this node.
    Explanation 2:
        The only half node present in the tree is 3 so we will remove this node.
<h2>Solution</h2>

***

```python
# Definition for a  binary tree node
# class TreeNode:
#    def __init__(self, x):
#        self.val = x
#        self.left = None
#        self.right = None

class Solution:
    # @param A : root node of tree
    # @return the root node in the tree
    def solve(self, A):
        if(not A):
            return None
        else:
            if(A.left and not A.right):
                return self.solve(A.left)
            elif(A.right and not A.left):
                return self.solve(A.right)
            A.left = self.solve(A.left)
            A.right = self.solve(A.right)
            return A
```
