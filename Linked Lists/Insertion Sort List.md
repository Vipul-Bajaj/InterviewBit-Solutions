<h1>Insertion Sort List</h1>

<p>
Sort a linked list using insertion sort.

We have explained Insertion Sort at Slide 7 of Arrays

Insertion Sort Wiki has some details on Insertion Sort as well.

<b>Example:</b>
    Input : 1 -> 3 -> 2
    Return 1 -> 2 -> 3
</p>

<h2>Solution</h2>

***

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
def sortedInsert(new_head,new_node):
    current = None
      
    # Special case for the head end */ 
    if (new_head == None or (new_head).val >= new_node.val): 
      
        new_node.next = new_head 
        new_head = new_node
      
    else: 
      
        # Locate the node before the point of insertion  
        current = new_head 
        while (current.next != None and
            current.next.val < new_node.val): 
          
            current = current.next
          
        new_node.next = current.next
        current.next = new_node 
          
    return new_head 

class Solution:
    # @param A : head node of linked list
    # @return the head node in the linked list
    def insertionSortList(self, A):
        curr = A
        new_head = None
        
        while curr:
            nextnode = curr.next
            new_head = sortedInsert(new_head,curr)
            curr = nextnode
            
        return new_head           
```