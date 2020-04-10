<h1>Max Sum Path in Binary Tree</h1>

<p>
Given a binary tree T, find the maximum path sum.

The path may start and end at any node in the tree.

Input Format:

    The first and the only argument contains a pointer to the root of T, A.
Output Format:

    Return an integer representing the maximum sum path.
Constraints:

    1 <= Number of Nodes <= 7e4
    -1000 <= Value of Node in T <= 1000
Example :

    Input 1:
         1
        / \
       2   3

    Output 1:
        6

    Explanation 1:
        The path with maximum sum is: 2 -> 1 -> 3

    Input 2:
        -10
        /  \
      -20  -30

    Output 2:
        -10

    Explanation 2
        The path with maximum sum is: -10

<h2>Solution</h2>

***

```python
# Definition for a  binary tree node
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
def findMaxUtil(root,res): 

    if root is None: 
        return 0 
  
    l = findMaxUtil(root.left,res) 
    r = findMaxUtil(root.right,res) 
      
    max_single = max(max(l, r) + root.val, root.val) 
      
    max_top = max(max_single, l+r+ root.val) 
  
    res[0] = max(res[0], max_top)  
  
    return max_single 

class Solution:
    # @param A : root node of tree
    # @return an integer
    def maxPathSum(self, A):
        res=[float("-inf")]
        findMaxUtil(A,res)
        return res[0]
```