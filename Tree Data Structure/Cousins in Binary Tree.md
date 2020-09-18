<h1>Cousins in Binary Tree</h1>

<p>
Given a Binary Tree A consisting of N nodes.

You need to find all the cousins of node B.

NOTE:

1. Siblings should not be considered as cousins.
2. Try to do it in single traversal.
3. You can assume that Node B is there in the tree A.
4. Order doesn't matter in the output.
Problem Constraints

    1 <= N <= 10^5
    1 <= B <= N
Input Format

    First Argument represents the root of binary tree A.
    Second Argument is an integer B denoting the node number.
Output Format
    
    Return an integer array denoting the cousins of node B.
    NOTE: Order doesn't matter.
Example:

    Input 1:
    A =
           1
         /   \
        2     3
       / \   / \
      4   5 6   7 
    B = 5
    Input 2:
    A = 
            1
          /   \
         2     3
        / \     \
       4   5     6
    B = 1
    Output 1:
    [6,7]
    Output 2:
    []
    Explanation 1:
    Cousins of Node 5 are Node 6 and 7 so we will return [6, 7]
    Remember Node 4 is sibling of Node 5 and do not need to return this.
    Explanation 2:
    Since Node 1 is the root so it doesn't have any cousin so we will return an empty array.

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
    # @param B : integer
    # @return a list of integers
    def solve(self, A, B):
        if A==B:
            return []
        q=[]
        res=[]
        q.append(A)
        boo=False
        i=1
        while(q and not boo):
            size=len(q)
            
            while(size):
                p=q[0]
                q=q[1:]
                
                if (p.left and p.left.val==B) or (p.right and p.right.val==B):
                    boo=True
    
                else:
                    if p.left:q.append(p.left)
                    if p.right:q.append(p.right)
                
                size-=1
            
        if boo:
            for i in q:
                res.append(i.val)
        return res
```
