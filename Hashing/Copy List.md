<h1>Copy List</h1>

<p>A linked list is given such that each node contains an additional random pointer which could point to any node in the list or NULL.

Return a deep copy of the list.

Example

Given list

    1 -> 2 -> 3
with random pointers going from

    1 -> 3
    2 -> 1
    3 -> 1
You should return a deep copy of the list. The returned answer should not contain the same node as the original list, but a copy of them. The pointers in the returned list should not link to any node in the original input list.
</p>

<h2>Solution</h2>

***

```python
# Definition for singly-linked list with a random pointer.
# class RandomListNode:
#     def __init__(self, x):
#         self.label = x
#         self.next = None
#         self.random = None
import random
class Solution:
    # @param head, a RandomListNode
    # @return a RandomListNode
    def copyRandomList(self, head):
        curr = head
        while curr != None: 
            new = RandomListNode(curr.label) 
            new.next = curr.next
            curr.next = new 
            curr = curr.next.next
      
        curr = head
        while curr != None: 
            curr.next.random = curr.random.next if curr.random else curr.random
            curr = curr.next.next
            
        curr = head
        dup_root = head.next
        while curr.next != None: 
            tmp = curr.next
            curr.next = curr.next.next
            curr = tmp 
      
        return dup_root 
```