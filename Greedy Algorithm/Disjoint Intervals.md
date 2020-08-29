<h1>Disjoint Intervals</h1>

<p>
Given a set of N intervals denoted by 2D array A of size N x 2, the task is to find the length of maximal set of mutually disjoint intervals.

Two intervals [x, y] & [p, q] are said to be disjoint if they do not have any point in common.

Return a integer denoting the length of maximal set of mutually disjoint intervals.

Problem Constraints

    1 <= N <= 105
    1 <= A[i][0] <= A[i][1] <= 109

Input Format:

    First and only argument is a 2D array A of size N x 2 denoting the N intervals.

Output Format:

    Return a integer denoting the length of maximal set of mutually disjoint intervals.

Example:

    Input 1:
        A = [
                [1, 4]
                [2, 3]
                [4, 6]
                [8, 9]
            ]
    Input 2:
        A = [
                [1, 9]
                [2, 3]
                [5, 7]
            ]
    Output 1:
        3
    Output 2:
        2
    Explanation 1:
        Intervals: [ [1, 4], [2, 3], [4, 6], [8, 9] ]
        Intervals [2, 3] and [1, 4] overlap.
        We must include [2, 3] because if [1, 4] is included thenwe cannot include [4, 6].
        We can include at max three disjoint intervals: [[2, 3], [4, 6], [8, 9]]
    Explanation 2:
        Intervals: [ [1, 9], [2, 3], [5, 7] ]
        We can include at max two disjoint intervals: [[2, 3], [5, 7]] 

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @return an integer
    def solve(self, A):
        n = len(A)
        A.sort(key=lambda x:x[1])
        endtime = A[0][1]
        count=1
        for i in range(1,n):
            if A[i][0]>endtime:
                count+=1
                endtime = A[i][1]
                
        return count
```