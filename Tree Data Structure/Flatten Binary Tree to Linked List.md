<h1>Flatten Binary Tree to Linked List</h1>

<p>
Given a binary tree, flatten it to a linked list in-place.

Example :
Given


         1
        / \
       2   5
      / \   \
     3   4   6
The flattened tree should look like:

    1
     \
      2
       \
        3
         \
          4
           \
            5
             \
              6
Note that the left child of all nodes should be NULL.
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
    # @return the root node in the tree
    def flatten(self, A):
        st = []
        last_node = None
        st.append(A)
        while st:
            if last_node:
                last_node.right = st[-1]
            last_node = st.pop(-1)
            left = last_node.left
            right = last_node.right
            last_node.left=None
            if right:
                st.append(right)
            if left:
                st.append(left)
                
        return A
                
```