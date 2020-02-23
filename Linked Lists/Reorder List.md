<h1>Reorder Listr</h1>

<p>
Given a singly linked list

    L: L0 → L1 → … → Ln-1 → Ln, 
reorder it to:

    L0 → Ln → L1 → Ln-1 → L2 → Ln-2 → …
You must do this in-place without altering the nodes’ values.

For example,
Given {1,2,3,4}, reorder it to {1,4,2,3}.
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
    def reorderList(self, A):
        slow = fast = A
        mid = None
        prev = None
        while fast and fast.next:
            prev = slow
            slow = slow.next
            fast = fast.next.next
            
        if fast:
            prev = slow
            mid = slow.next
        else:
            mid = slow
        new_prev = None
        while mid:
            new_next = mid.next
            mid.next = new_prev
            new_prev = mid
            mid = new_next
        
        prev.next = None
        
        mid = new_prev
        slow = A
        
        while slow and mid:
            new_next = slow.next
            slow.next = mid
            prev = mid.next
            mid.next = new_next
            slow = new_next
            mid = prev
            
        return A
```