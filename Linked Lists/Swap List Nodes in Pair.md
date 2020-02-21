<h1>Swap List Nodes in Pair</h1>

<p>
Given a linked list, swap every two adjacent nodes and return its head.

For example,
Given 1->2->3->4, you should return the list as 2->1->4->3.

Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.
</p>

<h2>Solution</h2>

***

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    # @param A : head node of linked list
    # @return the head node in the linked list
    def swapPairs(self, A):
        if A is None:
            return None
        if A and A.next == None:
            return A
            
        first = A
        second = first.next
        prev = A
        while second:
            if prev == A:
                A = second
            else:
                prev.next = second
            prev = first
            first.next = second.next
            second.next = first
            first = first.next
            if first == None:
                break
            second = first.next
        
        return A
```