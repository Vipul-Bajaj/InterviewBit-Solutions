<h1>Balance Array</h1>

<p>
Given an integer array A of size N. You need to count the number of special elements in the given array.
A element is special if removal of that element make the array balanced.

Array will be balanced if sum of even index element equal to sum of odd index element.

Problem Constraints

    1 <= N <= 10^5
    1 <= A[i] <= 10^9
Input Format

    First and only argument is an integer array A of size N.
Output Format
    
    Return an integer denoting the count of special elements.
Example:

    Input 1:
        A = [2, 1, 6, 4]
    Input 2:
        A = [5, 5, 2, 5, 8]
    Output 1:
        1
    Output 2:
        2
    Explanation 1:
        After deleting 1 from array : {2,6,4}
            (2+4) = (6)
        Hence 1 is the only special element, so count is 1
    Explanation 2:
        If we delete A[0] or A[1] , array will be balanced
            (5+5) = (2+8)
        So A[0] and A[1] are special elements, so count is 2.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def solve(self, A):
        n = len(A)
        even_sum = 0
        odd_sum = 0
        for i in range(n):
            if i%2==0:
                even_sum +=A[i]
            else:
                odd_sum +=A[i]
        
        ans = 0
        even = 0
        odd = 0
        for i in range(n):
            if i%2==0:
                even_sum-=A[i]
            else:
                odd_sum-=A[i]
            
            if even_sum+even == odd_sum+odd:
                ans+=1
            
            if i%2==0:
                odd+=A[i]
            else:
                even+=A[i]
            
        return ans
```