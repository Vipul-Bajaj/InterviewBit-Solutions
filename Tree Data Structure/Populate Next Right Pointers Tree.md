<h1>Populate Next Right Pointers Tree</h1>

<p>
Given a binary tree

    struct TreeLinkNode {
      TreeLinkNode *left;
      TreeLinkNode *right;
      TreeLinkNode *next;
    }
Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.

Initially, all next pointers are set to NULL.

    Note: You may only use constant extra space.

Example :

    Given the following binary tree,

                1
               /  \
              2    3
             / \  / \
            4  5  6  7

    After calling your function, the tree should look like:

                1 -> NULL
               /  \
              2 -> 3 -> NULL
             / \  / \
            4->5->6->7 -> NULL

    Note 1: that using recursion has memory overhead and does not qualify for constant space.
    Note 2: The tree need not be a perfect binary tree. 
</p>

<h2>Solution</h2>

***

```python
# Definition for a  binary tree node
# class TreeLinkNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
#         self.next = None

class Solution:
    # @param root, a tree node
    # @return nothing
    def connect(self, root):
        q = []
        q.append(root)
        currentLevelNode = 1
        nextLevelNode = 0
        prev = None
        while q:
            node = q.pop(0)
            if node.left:
                nextLevelNode+=1
                q.append(node.left)
            
            if node.right:
                nextLevelNode+=1
                q.append(node.right)
                
            if prev:
                prev.next = node
            
            prev = node
            currentLevelNode-=1
            
            if currentLevelNode == 0:
                currentLevelNode = nextLevelNode
                nextLevelNode = 0
                prev = None
                node.next = None
```