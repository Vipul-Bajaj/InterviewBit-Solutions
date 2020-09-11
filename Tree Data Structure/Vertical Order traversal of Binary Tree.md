<h1>Vertical Order traversal of Binary Tree</h1>

<p>
Given a binary tree A consisting of N nodes, return a 2-D array denoting the vertical order traversal of A.
Go through the example and image for more details.

NOTE:

    1. If 2 or more Tree Nodes shares the same vertical level then the one with earlier occurence in the pre-order traversal of tree comes first in the output.
    2. Row 1 of the output array will be the nodes on leftmost vertical line similarly last row of the output array will be the nodes on the rightmost vertical line.
Problem Constraints

    0 <= N <= 10^4
Input Format

    First and only argument is an pointer to root of the binary tree A.
Output Format
    
    Return a 2D array denoting the vertical order traversal of A.
Example:

    Input 1:
          6
        /   \
       3     7
      / \     \
     2   5     9
    Input 2:
           1
         /   \
        2     3
       / \
      4   5
    Output 1:
         [
            [2],
            [3],
            [6, 5],
            [7],
            [9]
         ]
    Output 2:
         [
            [4],
            [2],
            [1, 5],
            [3]
         ]
    Explanation 1:
        Nodes on Vertical Line 1: 2
        Nodes on Vertical Line 2: 3
        Nodes on Vertical Line 3: 6, 5
           As 6 and 5 are on the same vertical level but as 6 comes first in the pre-order traversal of the tree so we will output 6 before 5.
        Nodes on Vertical Line 4: 7
        Nodes on Vertical Line 5: 9
    Explanation 2:
        Nodes on Vertical Line 1: 4
        Nodes on Vertical Line 2: 2
        Nodes on Vertical Line 3: 1, 5
        Nodes on Vertical Line 4: 3

<h2>Solution</h2>

***

```python
# Definition for a  binary tree node
# class TreeNode:
#    def __init__(self, x):
#        self.val = x
#        self.left = None
#        self.right = None
def vertical(root,level,h,d):
    if root is None:
        return
    
    if level in d:
        d[level].append((root.val,h))
    else:
        d[level] = [(root.val,h)]
    
    if root.left:
        vertical(root.left,level-1,h+1,d)
    if root.right:
        vertical(root.right,level+1,h+1,d)
        
class Solution:
    # @param A : root node of tree
    # @return a list of list of integers
    def verticalOrderTraversal(self, A):
        d = {}
        
        vertical(A,0,0,d)
        
        ans = []
        
        for k in sorted(d.keys()):
            l = []
            for v in sorted(d[k],key=lambda x:x[1]):
                l.append(v[0])
            ans.append(l)
        return ans
```
