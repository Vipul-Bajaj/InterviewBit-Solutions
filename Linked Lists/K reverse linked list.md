<h1>K reverse linked list</h1>

<p>
Given a singly linked list and an integer K, reverses the nodes of the

list K at a time and returns modified linked list.

    NOTE :  
    1. The length of the list is divisible by K 
    2. Try to solve the problem using constant extra space.
</p>

<p><b>Example :</b>
<br>

    Given linked list 1 -> 2 -> 3 -> 4 -> 5 -> 6 and K=2,
    You should return 2 -> 1 -> 4 -> 3 -> 6 -> 5
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
    def reverseList(self, A, B):
        if B == 1:
            return A
        
        c = 0
        current = A
        new_prev = None
        first = True
        last = None
        while current:
            if c == B:
                c=0
                if first:
                    first = False
                    A = new_prev
                    
                else:
                    last.next = new_prev
                while new_prev:
                    last = new_prev
                    new_prev = new_prev.next
                new_prev = None
            new_next = current.next
            current.next = new_prev
            new_prev = current
            current = new_next
            c+=1
        if last:
            last.next = new_prev
        else:
            A = new_prev
            
        return A
```