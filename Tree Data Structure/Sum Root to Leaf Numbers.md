<h1>Sum Root to Leaf Numbers</h1>

<p>
Given a binary tree containing digits from 0-9 only, each root-to-leaf path could represent a number.

An example is the root-to-leaf path 1->2->3 which represents the number 123.

Find the total sum of all root-to-leaf numbers % 1003.

Example :

         1
        / \
       2   3
The root-to-leaf path 1->2 represents the number 12.
The root-to-leaf path 1->3 represents the number 13.

Return the sum = (12 + 13) % 1003 = 25 % 1003 = 25.
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
def sumToLeafNumber(node,arr,s):
    if node is None:
        return
    if node.left==None and node.right==None:
        arr.append(str(node.val))
        n = int(''.join(arr))
        s[0]+=n%1003
        arr.pop(-1)
        return
    arr.append(str(node.val))
    sumToLeafNumber(node.left,arr,s)
    sumToLeafNumber(node.right,arr,s)
    arr.pop(-1)
    
class Solution:
    # @param A : root node of tree
    # @return an integer
    def sumNumbers(self, A):
        s = [0]
        sumToLeafNumber(A,[],s)
        return s[0]%1003
```