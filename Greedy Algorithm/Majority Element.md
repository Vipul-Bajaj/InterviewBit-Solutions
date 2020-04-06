<h1>Majority Element</h1>

<p>Given an array of size n, find the majority element. The majority element is the element that appears more than floor(n/2) times.

You may assume that the array is non-empty and the majority element always exist in the array.

Example :

    Input : [2, 1, 2]
    Return  : 2 which occurs 2 times which is greater than 3/2. 

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @return an integer
    def majorityElement(self, A):
        ele = None
        count = 0
        for i in A:
            if count == 0:
                count+=1
                ele = i
            elif ele == i:
                count+=1
            else:
                count-=1
        count=0        
        for i in A:
            if i == ele:
                count+=1
        
        if count>= len(A)//2:
            return ele
        
        return -1
```