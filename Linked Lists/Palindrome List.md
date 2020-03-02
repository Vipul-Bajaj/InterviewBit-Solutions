<h1>Palindrome List</h1>

<p>
Given a singly linked list, determine if its a palindrome. Return 1 or 0 denoting if its a palindrome or not, respectively.

    Notes:
        1. Expected solution is linear in time and constant in space.

<b>For example:</b>

    List 1-->2-->1 is a palindrome.
    List 1-->2-->3 is not a palindrome.
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
    # @return an integer
    def lPalin(self, A):
        slow = A
        fast = A
        prev = A
        while fast and fast.next:
            prev = slow
            slow = slow.next
            fast = fast.next.next
        
        second_head = None    
        if fast:
            second_head = slow.next
        else:
            second_head = slow
        prev.next = None
            
        current = second_head
        previous,next = None,None
        while current:
            next = current.next
            current.next = previous
            previous = current
            current = next
        
        second_head = previous
        
        first = A
        second = second_head
        
        while first and second:
            if first.val != second.val:
                return 0
            first = first.next
            second = second.next
            
        return 1     
```