<h1>Sort Binary Linked List</h1>

<p>
Given a Linked List A consisting of N nodes.
The Linked List is binary i.e data values in the linked list nodes consist of only 0's and 1's.
You need to sort the linked list and return the new linked list.

NOTE:

    Try to do it in constant space.

Problem Constraints

    1 <= N <= 10^5
    A.val = 0 or A.val = 1
Input Format

    First and only argument is the head pointer of the linkedlist A.
Output Format
    
    Return the head pointer of the new sorted linked list.
Example:

    Input 1:
        1 -> 0 -> 0 -> 1
    Input 2:
        0 -> 0 -> 1 -> 1 -> 0
    Output 1:
        0 -> 0 -> 1 -> 1
    Output 2:
        0 -> 0 -> 0 -> 1 -> 1
    Explanation 1:
        The sorted linked list looks like:
            0 -> 0 -> 1 -> 1
    Explanation 2:
        The sorted linked list looks like:
            0 -> 0 -> 0 -> 1 -> 1

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
        n = 0
        count_0 = 0
        curr = A
        while curr:
            if curr.val==0:
                count_0+=1
            curr = curr.next
            n+=1
            
        c = 0
        curr = A
        while curr and c<count_0:
            curr.val = 0
            curr = curr.next
            c+=1
        
        while c<n and curr:
            curr.val = 1
            curr = curr.next
            c+=1
            
        return A
```