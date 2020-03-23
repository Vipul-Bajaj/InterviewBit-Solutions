<h1>BST Iterator</h1>

<p>
Implement an iterator over a binary search tree (BST). Your iterator will be initialized with the root node of a BST.

The first call to next() will return the smallest number in BST. Calling next() again will return the next smallest number in the BST, and so on.

    Note: next() and hasNext() should run in average O(1) time and uses O(h) memory, where h is the height of the tree.
    Try to optimize the additional space complexity apart from the amortized time complexity. 
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

class BSTIterator:
    # @param root, a binary search tree's root node
    def __init__(self, root):
        self.st = []
        node = root
        while node:
            self.st.append(node)
            node = node.left

    # @return a boolean, whether we have a next smallest number
    def hasNext(self):
        if self.st:
            return True
        return False

    # @return an integer, the next smallest number
    def next(self):
        node = self.st.pop(-1)
        val = node.val
        node = node.right
        while node:
            self.st.append(node)
            node = node.left
        return val
# Your BSTIterator will be called like this:
# i = BSTIterator(root)
# while i.hasNext(): print i.next(),
```