<h1>Level Order</h1>

<p>
Given a binary tree, return the level order traversal of its nodes’ values. (ie, from left to right, level by level).

Example :
    Given binary tree

           3
          / \
         9  20
           /  \
          15   7
    return its level order traversal as:

    [
        [3],
        [9,20],
        [15,7]
    ]

Also think about a version of the question where you are asked to do a level order traversal of the tree when depth of the tree is much greater than number of nodes on a level.

<h2>Solution</h2>

***

```python
# Definition for a  binary tree node
# class TreeNode:
#	def __init__(self, x):
#		self.val = x
#		self.left = None
#		self.right = None

class Solution:
	# @param A : root node of tree
	# @return a list of list of integers
	def levelOrder(self, A):
	    ans = []
        q = []
        q.append(A)
        q.append(None)
        l = []
        while q:
            node = q.pop(0)
            
            if node:
                l.append(node.val)
                if node.left:
                    q.append(node.left)
                if node.right:
                    q.append(node.right)
            else:
                if q:
                    q.append(None)
                ans.append(l)
                l =[]
                 
        return ans
```