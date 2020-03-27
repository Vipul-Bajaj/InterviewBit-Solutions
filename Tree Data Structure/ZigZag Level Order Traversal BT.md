<h1>ZigZag Level Order Traversal BT</h1>

<p>
Given a binary tree, return the zigzag level order traversal of its nodes’ values. (ie, from left to right, then right to left for the next level and alternate between).

Example :

Given binary tree

         3
        / \
       9  20
      /     \
     15      7
    
return

    [
        [3],
        [20, 9],
        [15, 7]
    ]
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
    # @return a list of list of integers
    def zigzagLevelOrder(self, A):
        st = [A]
        st1 = []
        res = []
        row = []
        while st or st1:
            while st:
                node  = st.pop(0)
                row.append(node.val)
                if node.left:
                    st1.insert(0,node.left)
                if node.right:
                    st1.insert(0,node.right)
                    
            if row:
                res.append(row)
            row = []
            while st1:
                node = st1.pop(0)
                row.append(node.val)
                if node.right:
                    st.insert(0,node.right)
                if node.left:
                    st.insert(0,node.left)
            if row:
                res.append(row)
            row = []
                    
        return res
```