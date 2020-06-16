<h1>Delete and Conquer</h1>

<p>
Given an array A of N integers, you are allowed to create a new array B by deleting some (possibly none) elements from array A.

What are the minimum number of elements you have to delete from the A to get B such that every element in B is divisble by every other element in B.

Constraints:

    1.   1 <= N <= 100000
    2.   1 <= A[i] <= 1000000000
Input:

    A single array A.

Output:

    Minimum number of elements to delete from A such that every element in the new array is divisble by every other element in the new array

Example:

    Input:
        A : 10 20 10 20 10 5
    Output:
        3
Explanation:

    The optimal choice is to delete the two 20's and the single 5 so as to get B as :10 10 10.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def deleteandconquer(self, A):
        hashmap = {}
        for i in A:
            if i in hashmap:
                hashmap[i]+=1
            else:
                hashmap[i]=1
        
        max_value = max(list(hashmap.values()))
        
        return len(A)-max_value
```