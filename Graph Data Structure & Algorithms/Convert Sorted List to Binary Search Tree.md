<h1>Convert Sorted List to Binary Search Tree</h1>

<p>
Given a singly linked list where elements are sorted in ascending order, convert it to a height balanced BST.

    A height balanced BST : a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1. 

Example :

    A height balanced BST  :
    Given A : 1 -> 2 -> 3
          2
        /   \
       1     3

<h2>Solution</h2>

***

```python
# Definition for a  binary tree node
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

def func(head,low,high):
    
    if head is None or low>high:
        return None
    
    curr = head
    count = 0
    mid = (low+high)//2
    while curr and count<mid:
        curr = curr.next
        count+=1
    if curr:    
        node = TreeNode(curr.val)
        node.left = func(head,0,mid-1)
        node.right = func(curr.next,0,high-(mid+1))
        return node
    return None
    
    
class Solution:
    # @param A : head node of linked list
    # @return the root node in the tree
    def sortedListToBST(self, A):
        len_of_ll = 0
        
        curr = A
        while curr:
            len_of_ll+=1
            curr=curr.next
        
        return func(A,0,len_of_ll-1)
```