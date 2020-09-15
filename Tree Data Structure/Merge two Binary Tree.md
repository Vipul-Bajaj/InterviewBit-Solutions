<h1>Merge two Binary Tree</h1>

<p>
Given two Binary Trees A and B, you need to merge them in a single binary tree.
The merge rule is that if two nodes overlap, then sum of node values is the new value of the merged node.
Otherwise, the non-null node will be used as the node of new tree.
Problem Constraints

    1 <= Number of Nodes in A , B <= 10^5
Input Format

    First argument is an pointer to the root of binary tree A.
    Second argument is an pointer to the root of binary tree B.
Output Format
    
    Return a pointer to the root of new binary tree.
Example:

    Input 1:
    A =    2
          / \
         1   4
        /
       5
    B =    3
          / \
         6   1
          \   \
           2   7
    Input 2:
    A =    12
          / \
        11  14            
    B =    3
          / \
         6   1
    Output 1:
         5
        / \
       7   5
      / \   \ 
     5   2   7
    Output 2:
       15
      / \
     17  15
    Explanation 1:
     After merging both the trees you get:
         5
        / \
       7   5
      / \   \ 
     5   2   7
    Explanation 2:
    After merging both the trees we get:
       15
      / \
     17  15

<h2>Solution</h2>

***

```python
# Definition for a  binary tree node
# class TreeNode:
#    def __init__(self, x):
#        self.val = x
#        self.left = None
#        self.right = None
def merge(t1,t2):
    if (not t1):  
        return t2  
    if (not t2): 
        return t1  
    t1.val += t2.val  
    t1.left = merge(t1.left, t2.left)  
    t1.right = merge(t1.right, t2.right)  
    return t1 
class Solution:
    # @param A : root node of tree
    # @param B : root node of tree
    # @return the root node in the tree
    def solve(self, A, B):
        if A is None:
            return B
        if B is None:
            return A
        
        return merge(A,B)
```
