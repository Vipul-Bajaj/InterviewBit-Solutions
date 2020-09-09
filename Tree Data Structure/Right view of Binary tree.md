<h1>Right view of Binary tree</h1>

<p>
Given a binary tree A of integers. Return an array of integers representing the right view of the Binary tree.

Right view of a Binary Tree: is a set of nodes visible when the tree is visited from Right side.

Problem Constraints

    1 <= Number of nodes in binary tree <= 105
    0 <= node values <= 10^9
Input Format

    First and only argument is an pointer to the root of binary tree A.
Output Format
    
    Return an integer array denoting the right view of the binary tree A.
Example:

    Input 1:
            1
          /   \
         2     3
        / \   / \
       4   5 6   7
      /
     8 
    Input 2:
        1
       /  \
      2    3
       \
        4
         \
          5
    Output 1:
        [1, 3, 7, 8]
    Output 2:
        [1, 3, 4, 5]

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
        ans = []
        while q:
            n = len(q)
            
            for i in range(1,n+1):
                node = q.popleft()
                if i == n:
                    ans.append(node.val)
                    
                if node.left:
                    q.append(node.left)
                if node.right:
                    q.append(node.right)
            
        return ans
```
