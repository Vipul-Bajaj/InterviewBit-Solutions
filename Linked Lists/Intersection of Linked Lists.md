<h1>Intersection of Linked Lists</h1>

<p>
Write a program to find the node at which the intersection of two singly linked lists begins.

For example, the following two linked lists:

    A:          a1 → a2
                        ↘
                            c1 → c2 → c3
                        ↗
    B:     b1 → b2 → b3

begin to intersect at node c1.

     Notes:
        1. If the two linked lists have no intersection at all, return null.
        2. The linked lists must retain their original structure after the function returns.
        3. You may assume there are no cycles anywhere in the entire linked structure.
        4. Your code should preferably run in O(n) time and use only O(1) memory.
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
    def getIntersectionNode(self, A, B):
        len_A = 0
        len_B = 0
        
        curr = A
        
        while curr:
            curr = curr.next
            len_A+=1
            
        curr = B
        
        while curr:
            curr = curr.next
            len_B+=1
            
        d=len_A-len_B
        if len_B>len_A:
           d = len_B-len_A 
        c = 0   
        curr_A = A
        curr_B = B
        if len_A>len_B:
            curr_A = A
            curr_B = B
            while c<d:
                curr_A = curr_A.next
                c+=1
        else:
            curr_A = A
            curr_B = B
            while c<d:
                curr_B = curr_B.next
                c+=1
        
        while curr_A and curr_B:
            if curr_A == curr_B:
                return curr_A
                
            curr_A = curr_A.next
            curr_B = curr_B.next
            
        return None
                
```