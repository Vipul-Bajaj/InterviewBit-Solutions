<h1>Maximum level sum</h1>

<p>
Given a Binary Tree denoted by root node A having integer value on nodes. You need to find maximum sum level in it.

Problem Constraints

    1 <= number of nodes <= 10^5
    1 <= value on nodes <= 10^5
Input Format

    First and only argument is a root node of Binary Tree A.
Output Format
    
    Return an integer denoting the maximum sum level in the tree.
Example:

    Input 1:
            4
          /   \
         2     5
        / \   / \
       1  3  2   6
    Input 2:
            1
          /   \
         2     3
       /  \     \
      4    5     8
                / \
               6   7  
    Output 1:
        12
    Output 2:
        17
    Explanation 1:
        Sum of all nodes of 0'th level is 4 
        Sum of all nodes of 1'th level is 7
        Sum of all nodes of 2'th level is 12
        Hence maximum sum is 12
    Explanation 2:
        Sum of all nodes of 0'th level is 1
        Sum of all nodes of 1'th level is 5
        Sum of all nodes of 2'th level is 17
        Sum of all nodes of 3'th level is 13
        Hence maximum sum is 17
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
    # @return an integer
    def solve(self, A):
        q = [A,None]
        max_sum = 0
        s=0
        while q:
            node = q.pop(0)
            if node:
                s+=node.val
                if node.left:
                    q.append(node.left)
                if node.right:
                    q.append(node.right)
            else:
                max_sum = max(s,max_sum)
                s=0
                if not q:
                    break
                q.append(None)
        return max_sum
```
