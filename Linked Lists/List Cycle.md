<h1>List Cycle</h1>

<p>Given a linked list, return the node where the cycle begins. If there is no cycle, return null.

Try solving it using constant additional space.</p>

<p><b>Example :</b>
<br>
    Input : 

                  ______
                 |     |
                 \/    |
        1 -> 2 -> 3 -> 4

    Return the node corresponding to node 3.
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
    # @return the first node in the cycle in the linked list
    def detectCycle(self, A):
        slow = A
        fast = A
        cycle = False
        while slow and fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            if slow == fast:
                cycle = True
                break
            
        if cycle == True:
            slow = A
            while slow != fast:
                fast = fast.next
                slow = slow.next
            return slow
        else:
            return None
```