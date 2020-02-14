<h1>Painters Partition Problem</h1>

<p>
Given an array of integers A of size N and an integer B.

College library has N bags,the ith book has A[i] number of pages.

You have to allocate books to B number of students so that maximum number of pages alloted to a student is minimum.

    A book will be allocated to exactly one student.
    Each student has to be allocated at least one book.
    Allotment should be in contiguous order, for example: A student cannot be allocated book 1 and book 3, skipping book 2.
Calculate and return that minimum possible number.

NOTE: Return -1 if a valid assignment is not possible.
</p>

<p><b>Example :</b>
<br>

```python
Input 1:
    A = [12, 34, 67, 90]
    B = 2
Output 1:
    113
Explanation 1:
    There are 2 number of students. Books can be distributed in following fashion : 
        1) [12] and [34, 67, 90]
        Max number of pages is allocated to student 2 with 34 + 67 + 90 = 191 pages
        2) [12, 34] and [67, 90]
        Max number of pages is allocated to student 2 with 67 + 90 = 157 pages 
        3) [12, 34, 67] and [90]
        Max number of pages is allocated to student 1 with 12 + 34 + 67 = 113 pages

        Of the 3 cases, Option 3 has the minimum pages = 113.

Input 2:
    A = [5, 17, 100, 11]
    B = 4
Output 2:
    100
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return an integer
    def books(self, A, B):
        n = len(A)
        mod = 10000003
        
        if n<1 or n<B:
            return -1
            
        l,h = max(A) , sum(A)
        
        while(l<h):
            mid = (l+h)//2
            
            r = 1
            cl = 0
            
            for i in range(n):
                if cl + A[i] <=mid:
                    cl+=A[i]
                else:
                    r+=1
                    cl = A[i]
                    
            if r<=B:
                h=mid
            else:
                l=mid+1
                
        return l
```