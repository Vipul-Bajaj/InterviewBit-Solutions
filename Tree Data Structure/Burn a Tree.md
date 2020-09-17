<h1>Burn a Tree</h1>

<p>
Given a binary tree denoted by root node A and a leaf node B from this tree.
It is known that all nodes connected to a given node (left child, right child and parent) get burned in 1 second. Then all the nodes which are connected through one intermediate get burned in 2 seconds, and so on.
You need to find the minimum time required to burn the complete binary tree.

Problem Constraints

    2 <= number of nodes <= 10^5
    1 <= node value, B <= 10^5
    node value will be distinct
    
Input Format

    First argument is a root node of the binary tree, A.
    Second argument is an integer B denoting the node value of leaf node.
    
Output Format
    
    Return an integer denoting the minimum time required to burn the complete binary tree.
Example:

    Input 1:
    Tree :      1 
               / \ 
              2   3 
             /   / \
            4   5   6
    B = 4
    Input 2:
    Tree :      1
               / \
              2   3
             /     \
            4       5 
    B = 5
    Output 1:
    4
    Output 2:
    4
    Explanation 1:
    After 1 sec: Node 4 and 2 will be burnt. 
    After 2 sec: Node 4, 2, 1 will be burnt.
    After 3 sec: Node 4, 2, 1, 3 will be burnt.
    After 4 sec: Node 4, 2, 1, 3, 5, 6(whole tree) will be burnt.
    Explanation 2:
    After 1 sec: Node 5 and 3 will be burnt. 
    After 2 sec: Node 5, 3, 1 will be burnt.
    After 3 sec: Node 5, 3, 1, 2 will be burnt.
    After 4 sec: Node 5, 3, 1, 2, 4(whole tree) will be burnt.

<h2>Solution</h2>

***

```python
# Definition for a  binary tree node
# class TreeNode:
#    def __init__(self, x):
#        self.val = x
#        self.left = None
#        self.right = None
import sys
sys.setrecursionlimit(10000000)
def dfs(A,B,h,ans):
    if not A:
        return False
    
    hr=[0]
    hl=[0]
    
    leftfire = False
    rightfire = False
    
    leftfire = dfs (A.left,B, hl, ans)
    rightfire = dfs (A.right,B, hr, ans)
    
    if (not leftfire and not rightfire):
        h[0] = max (hr[0],hl[0]) + 1
    elif (leftfire):
        h[0] = hl[0]+1
    else:
        h[0] = hr[0] +1
    
    if (B == A.val or leftfire or rightfire):
        ans[0] = max (ans[0], hr[0] + hl[0] + 1)
        return True
    return False
    
class Solution:
    # @param A : root node of tree
    # @param B : integer
    # @return an integer
    def solve(self, A, B):
        ans = [0]
        dfs(A,B,[0],ans)
        return ans[0]-1
```
