<h1>Remove Duplicates From Sorted List</h1>

<p>
Given a sorted linked list, delete all duplicates such that each element appear only once.
</p>

<p><b>Example :</b>
<br>

    Given 1->1->2, return 1->2.
    Given 1->1->2->3->3, return 1->2->3.
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
    def deleteDuplicates(self, A):
        if A is None:
            return A
        
        prev = A
        current = A
        
        while current.next:
            current = current.next
            if prev.val == current.val:
                prev.next = current.next
            else:
                prev = current
                
        return A
```