<h1>Remove Duplicates From Sorted List II</h1>

<p>
Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list.
</p>

<p><b>Example :</b>
<br>

    Given 1->1->2, return 2.
    Given 1->1->2->3->3, return 2.
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
        current = A
        isDuplicate = False
        A = prev = ListNode(None)
        
        while current != None:
            if current.next != None and current.val == current.next.val:
                isDuplicate = True
            elif isDuplicate:
                isDuplicate = False
            else:
                prev.next = current
                prev = current
            current = current.next
        
        prev.next = current
        
        return A.next
```