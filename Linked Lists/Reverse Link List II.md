<h1>Reverse Link List II</h1>

<p>
Reverse a linked list from position m to n. Do it in-place and in one-pass.

    Note:
    1. Given m, n satisfy the following condition:
       1 ≤ m ≤ n ≤ length of list. 
    2. Usually the version often seen in the interviews is reversing the whole linked list which is obviously an easier version of this question. 
</p>

<p><b>Example :</b>
<br>

    Given 1->2->3->4->5->NULL, m = 2 and n = 4,
    return 1->4->3->2->5->NULL.
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
    # @param C : integer
    # @return the head node in the linked list
    def reverseBetween(self, A, B, C):
        if A is None:
            return
        
        prev = A
        current = A
        c = 1
        
        while current and c<B:
            prev = current
            current = current.next
            c+=1
            
        new_prev = None
        while current and c<=C:
            new_next = current.next
            current.next = new_prev
            new_prev = current
            current = new_next
            c+=1
        
        if B == 1:
            A = new_prev
        else:
            prev.next = new_prev
        
        while new_prev.next:
            new_prev = new_prev.next
        new_prev.next = current
        
        return A
```