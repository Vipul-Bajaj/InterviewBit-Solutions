<h1>Rotate List</h1>

<p>
Given a list, rotate the list to the right by k places, where k is non-negative.
</p>

<p><b>Example :</b>
<br>

    Given 1->2->3->4->5->NULL and k = 2,
    return 4->5->1->2->3->NULL.
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
    def rotateRight(self, A, B):
        len_of_ll = 0
        
        if A is None:
            return None
            
        current = A
        while current:
            len_of_ll+=1
            current = current.next
            
        B = B%len_of_ll
        if B == 0:
            return A
        prev = None
        current = A
        count = 0
        while count<len_of_ll-B and current:
            prev = current
            current = current.next
            count+=1
        
        prev.next = None
        prev = current
        while current.next:
            current = current.next
        current.next = A
        A = prev
        
        return A
```