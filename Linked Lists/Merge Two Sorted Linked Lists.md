<h1>Merge Two Sorted Linked Lists</h1>

<p>
Merge two sorted linked lists and return it as a new list.
The new list should be made by splicing together the nodes of the first two lists, and should also be sorted.
</p>

<p><b>For example, given following linked lists :</b>
<br>

    5 -> 8 -> 20 
    4 -> 11 -> 15
</p>
<p><b>The merged list should be :</b>
<br>

    4 -> 5 -> 8 -> 11 -> 15 -> 20
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
    # @param B : head node of linked list
    # @return the head node in the linked list
    def mergeTwoLists(self, A, B):
        new_head,new_tail = None,None
        
        first = A
        second = B
        
        while first and second:
            if first.val<=second.val:
                if new_head == None:
                    new_head = new_tail = ListNode(first.val)
                else:
                    new_tail.next = ListNode(first.val)
                    new_tail = new_tail.next
                first = first.next    
            else:
                if new_head == None:
                    new_head = new_tail = ListNode(second.val)
                else:
                    new_tail.next = ListNode(second.val)
                    new_tail = new_tail.next
                second = second.next    
                
        while first:
            if new_head == None:
                new_head = new_tail = ListNode(first.val)
            else:
                new_tail.next = ListNode(first.val)
                new_tail = new_tail.next
            first = first.next    
        
        while second:
            if new_head == None:
                new_head = new_tail = ListNode(second.val)
            else:
                new_tail.next = ListNode(second.val)
                new_tail = new_tail.next
            second = second.next    
            
        return new_head
```