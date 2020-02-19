<h1>Add Two Numbers as Lists</h1>

<p>
You are given two linked lists representing two non-negative numbers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
</p>

<p><b>Example :</b>
<br>

    342 + 465 = 807
</p>

<p>
Make sure there are no trailing zeros in the output list
So, 7 -> 0 -> 8 -> 0 is not a valid response even though the value is still 807.
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
    def addTwoNumbers(self, A, B):
        first = A
        second = B
        carry = 0
        prev = None
        
        while first and second:
            val1 = first.val
            val2 = second.val
            ans = val1 + val2 + carry
            carry = ans//10
            ans = ans%10
            first.val = ans
            prev = first
            first = first.next
            second = second.next
            
        while second:
            val2 = second.val
            ans = val2 + carry
            carry = ans//10
            ans = ans%10
            node = ListNode(ans)
            prev.next = node
            prev = node
            second = second.next
            
        while first:
            val1 = first.val
            ans = val1 + carry
            carry = ans//10
            ans = ans%10
            first.val = ans
            prev = first
            first = first.next
            
        if carry:
            node = ListNode(carry)
            prev.next = node
            
        return A
```