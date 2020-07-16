<h1>Meeting rooms</h1>

<p>
Given an 2D integer array A of size N x 2 denoting time intervals of different meetings.

Where:

1. A[i][0] = start time of the ith meeting.
2. A[i][1] = end time of the ith meeting.

Find the minimum number of conference rooms required so that all meetings can be done.

Problem Constraints

    1 <= N <= 10

    0 <= A[i][0] < A[i][1] <= 2 * 10^9
Input Format

    The only argument given is the matrix A.
Output Format
    
    Return the minimum number of conference rooms required so that all meetings can be done.
Example:

    Input 1:
        A = [      
                [0, 30]
                [5, 10]
                [15, 20]
            ]
    Input 2:
        A = [     
                [1, 18]
                [18, 23]
                [15, 29]
                [4, 15]
                [2, 11]
                [5, 13]
            ]
    Output 1:
        2
    Output 2:
        4
    Explanation 1:
        Meeting one can be done in conference room 1 form 0 - 30.
        Meeting two can be done in conference room 2 form 5 - 10.
        Meeting one can be done in conference room 2 form 15 - 20 as it is free in this interval.
    Explanation 2:
        Meeting one can be done in conference room 1 from 1 - 18.
        Meeting five can be done in conference room 2 from 2 - 11.
        Meeting four can be done in conference room 3 from 4 - 15.
        Meeting six can be done in conference room 4 from 5 - 13.
        Meeting three can be done in conference room 2 from 15 - 29 as it is free in this interval.
        Meeting two can be done in conference room 4 from 18 - 23 as it is free in this interval.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @return an integer
    def solve(self, A):
        arr = []
    
        for x,y in A:
            arr.append([x,1])
            arr.append([y,-1])
            
        arr.sort()
        
        max_sum = 0
        
        max_sum_ending_here = 0
    
        for x,y in arr:
            max_sum_ending_here += y
            
            if max_sum<max_sum_ending_here:
                max_sum = max_sum_ending_here
                
            if max_sum_ending_here<0:
                max_sum_ending_here = 0
                
        return max_sum
```