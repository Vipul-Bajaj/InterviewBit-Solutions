<h1>Reverse Level Order</h1>

<p>
Given a binary tree, return the reverse level order traversal of its nodes values. (i.e, from left to right and from last level to starting level).

Problem Constraints

    1 <= number of nodes <= 5 * 10^5
    1 <= node value <= 10^5
Input Format

    First and only argument is a pointer to the root node of the Binary Tree, A.
Output Format
    
    Return an integer array denoting the reverse level order traversal from left to right.
Example:

    Input 1:
         3
        / \
       9  20
         /  \
        15   7
    Input 2:
        1
       / \
      6   2
         /
        3
    Output 1:
        [15, 7, 9, 20, 3] 
    Output 2:
        [3, 6, 2, 1]
    Explanation 1:
        Nodes as level 3 : [15, 7]
        Nodes at level 2: [9, 20]
        Nodes at level 1: [3]
        Reverse level order traversal will be: [15, 7, 9, 20, 3]
    Explanation 2:
        Nodes as level 3 : [3]
        Nodes at level 2: [6, 2]
        Nodes at level 1: [1]
        Reverse level order traversal will be: [3, 6, 2, 1]

<h2>Solution</h2>

***

```python
from collections import deque
# Definition for a  binary tree node
# class TreeNode:
#    def __init__(self, x):
#        self.val = x
#        self.left = None
#        self.right = None

class Solution:
    # @param A : root node of tree
    # @return a list of integers
    def solve(self, A):
        q = deque([A])
        ans = deque([])
        while q:
            node = q.popleft()
            ans.appendleft(node.val)
            if node.right:
                q.append(node.right)
            if node.left:
                q.append(node.left)
                
        return ans
```