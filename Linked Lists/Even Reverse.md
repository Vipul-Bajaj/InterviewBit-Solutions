<h1>Even Reverse</h1>

<p>
Given a linked list A , reverse the order of all nodes at even positions.

Problem Constraints

    1 <= Size of linked list <= 100000
Input Format

    First and only argument is the head of the Linked-List A.

Output Format
    
    Return the head of the new linked list.
Example:

    Input 1:
        A = 1 -> 2 -> 3 -> 4
    Input 2:
        A = 1 -> 2 -> 3
    Output 1:
        1 -> 4 -> 3 -> 2
    Output 2:
        1 -> 2 -> 3
    Explanation 1:
        Nodes are positions 2 and 4 have been swapped.
    Explanation 2:
        No swapping neccassary here.

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
    def solve(self, A):
        current = A
        even_head = None
        even_tail = None
        previous = None
        while current:
            previous = current
            current = current.next
            if even_head is None:
                even_head = even_tail = current
            else:
                even_tail.next = current
                even_tail = current
            previous.next = current.next if current else None
            current = current.next if current else None

        current = even_head
        previous = None
        next = None
        while current:
            next = current.next
            current.next = previous
            previous = current
            current = next

        first = A
        last = previous
        while first and last:
            previous = first
            temp = first.next
            temp1 = last.next
            first.next = last
            first.next.next = temp
            first = first.next.next
            last = temp1
            
        return A
```