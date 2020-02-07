<h1>Merge Two Sorted Lists II</h1>

<p>
Given two sorted integer arrays A and B, merge B into A as one sorted array.

Note: You have to modify the array A to contain the merge of A and B. Do not output anything in your code.
TIP: C users, please malloc the result into a new array and return the result. 
If the number of elements initialized in A and B are m and n respectively, the resulting size of array A after your code is executed should be m + n
</p>

<p><b>Example :</b>
<br>
Input : 
         A : [1 5 8]
         B : [6 9]

<br>
Modified A : [1 5 6 8 9]
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : list of integers
    def merge(self, A, B):
        i = 0
        j = 0
        while i < len(A) and j < len(B):
            while i < len(A) and A[i] < B[j]:
                i += 1
            A.insert(i, B[j])
            j += 1
            i += 1
        print(" ".join([str(x) for x in A]) + " ")
```