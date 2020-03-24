<h1>Root to Leaf Paths With Sum</h1>

<p>
Given a binary search tree T, where each node contains a positive integer, and an integer K, you have to find whether or not there exist two different nodes A and B such that A.value + B.value = K.

Return 1 to denote that two such nodes exist. Return 0, otherwise.

Notes

Your solution should run in linear time and not take memory more than O(height of T).
Assume all values in BST are distinct.

<b>Example :</b>

    Input 1: 

        T :      10
                /  \
               9   20

        K = 19

        Return: 1

    Input 2: 

        T:        10
                 /  \
                9   20

        K = 40

        Return: 0
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
    # @param B : integer
    # @return an integer
    def TwoSumBinary(self,node,k,sum_set):
        if node == None:
            return 0
        if self.TwoSumBinary(node.left,k,sum_set):
            return 1
        if sum_set and k-node.val in sum_set:
            return 1
        else:
            sum_set.add(node.val)
        return self.TwoSumBinary(node.right,k,sum_set)
        
    def t2Sum(self, A, B):
        sum_set = set()
        return self.TwoSumBinary(A,B,sum_set)
```