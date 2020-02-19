<h1>Remove Nth Node from List End</h1>

<p>
Given a linked list, remove the nth node from the end of list and return its head.

    Note:
        1. If n is greater than the size of the list, remove the first node of the list.
</p>

<p><b>Example :</b>
<br>

    Given linked list: 1->2->3->4->5, and n = 2.
    After removing the second node from the end, the linked list becomes 1->2->3->5.
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
    # @param B : integer
    # @return the head node in the linked list
    def removeNthFromEnd(self, A, B):
        if A is None:
            return A

        count = 0
        current = A
        while current:
            count+=1
            current = current.next
            
        if B>=count:
            A = A.next
            return A
        
        c = 0    
        current = A
        while c<count-B and current:
            prev = current
            current = current.next
            c+=1
            
        prev.next = current.next
        
        return A
```