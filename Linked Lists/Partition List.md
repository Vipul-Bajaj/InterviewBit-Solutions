<h1>Partition List</h1>

<p>
Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.

You should preserve the original relative order of the nodes in each of the two partitions.
</p>

<p><b>Example :</b>
<br>

    Given 1->4->3->2->5->2 and x = 3,
    return 1->2->2->4->3->5.
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
    def partition(self, A, B):
        if A is None:
            return
        new_head_1,new_tail_1 = None,None
        new_head_2,new_tail_2 = None,None
        
        current = A

        while current:
            if current.val<B:
                if new_head_1 is None:
                    new_head_1 = new_tail_1 = ListNode(current.val)
                else:
                    new_tail_1.next = ListNode(current.val)
                    new_tail_1 = new_tail_1.next
            else:
                if new_head_2 is None:
                    new_head_2 = new_tail_2 = ListNode(current.val)
                else:
                    new_tail_2.next = ListNode(current.val)
                    new_tail_2 = new_tail_2.next
            current = current.next    
            
        if new_head_1:
            A = new_head_1
            new_tail_1.next = new_head_2
        else:
            A = new_head_2
            new_tail_2.next = new_head_1
        
        return A
```