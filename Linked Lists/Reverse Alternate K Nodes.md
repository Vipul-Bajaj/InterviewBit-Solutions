<h1>Reverse Alternate K Nodes</h1>

<p>
Given a linked list A of length N and an integer B.

You need to reverse every alternate B nodes in the linked list A.

Problem Constraints

    1 <= N <= 10^5
    1<= Value in Each Link List Node <= 10^3
    1 <= B <= N
    N is divisible by B
Input Format

    First argument is the head pointer of the linkedlist A.
    Second argument is an integer B.

Output Format
    
    Return the head pointer of the final linkedlist as described.
Example:

    Input 1:
        A = 3 -> 4 -> 7 -> 5 -> 6 -> 6 -> 15 -> 61 -> 16
        B = 3
    Input 2:
        A = 1 -> 14 -> 6 -> 6 -> 4 -> 10
        B = 2
    Output 1:
        7 -> 4 -> 3 -> 5 -> 6 -> 6 -> 16 -> 61 -> 15
    Output 2:
        4 -> 1 -> 6 -> 6 -> 10 -> 4
    Explanation 1:
        The linked list contains 9 nodes and we need to reverse alternate 3 nodes.
        First sublist of length 3  is 3 -> 4 -> 7 so on reversing it we get 7 -> 4 -> 3.
        Second sublist of length 3 is 5 -> 6 -> 6 we don't need to reverse it.
        Third sublist of length 3 is 15 -> 61 -> 16 so on reversing it we get 16 -> 61 -> 15
    Explanation 2:
        The linked list contains 6 nodes and we need to reverse alternate 2 nodes.
        First sublist of length 2 is 1 -> 4 so on reversing it we get 4 -> 1.
        Second sublist of length 2 is 6 -> 6 we don't need to reverse it.
        Third sublist of length 2 is 4 -> 10 so on reversing it we get 10 -> 4.

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
    def solve(self, A, B):
        current = A
        previous = None
        length = 0
        while current:
            current = current.next
            length+=1
          
        n = 0
        head_changed = False
        current = A
        previous = None
        last_previous = None
        while n<length:
            
            last_node = None
            got_last_node = False
            
            c = 0 
            
            while current and c<B:
                next = current.next
                current.next = previous
                previous = current
                if not got_last_node:
                    last_node = previous
                    got_last_node = True
                current = next
                c+=1
                n+=1
            
            if not head_changed:
                A = previous
                head_changed = True
            else:
                last_previous.next = previous
                
            last_node.next = current
            
            c = 0    
            
            while current and c<B:
                last_previous = current
                current = current.next
                c+=1
                n+=1
        return A
```