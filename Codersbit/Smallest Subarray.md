<h1>Smallest Subarray</h1>

<p>
Scooby and Shaggy are best of friends and also very good programmers, so they keep challenging each other with interesting
questions. Scooby gives the following question to Shaggy :

Given an array A consisting of N positive integers, what is the length of the smallest sub array of A whose sum
is greater than or equal to a given integer K. If there is no such sub array of A with sum greater than or equal to K
then return -1.

As Shaggy is preparing for his placements, he wants you to find the answer to the above question.

    Note: A subarray is a contiguous part of array.

Constraints:

    Number of testcases T: 1<=T<=10 
    Length of the array N: 1<=N<=100000
    Elements of the array: 1<=A[i]<=10000
    1<=K<=1000000000

Input:

    An integer array A
    An integer K

Note:

    Your code will run against multiple testcases.

Output:

    One integer corresponding to the length of the smallest sub array of A with sum greater than or equal to K.
    If there is no such sub array with sum greater than or equal to K return -1.

Examples:

    Input:
        1 2 3 4 5
        7
    Output:
        2
    Explanation:
        Following sub arrays have sum greater than or equal to given K i.e 7:
        [1,2,3,4]
        [1,2,3,4,5]
        [2,3,4]
        [2,3,4,5]
        [3,4]
        [3,4,5]
        [4,5]
        Out of these sub arrays the smallest subarray with sum greater than or equal to 7 is of length 2([3,4] or [4,5]) and hence 
        the answer is 2.
    Input:
        3 1 6 2
        14
    Output:
        -1
    Explanation:
        There is no sub array with sum greater than or equal to 14
    Input:
        3 1 4
        8
    Output:
        3
    Explanation:
        The only sub array with sum greater than or equal to 8 is the whole array [3,1,4] itself. Therefore the answer is 3. 
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : integer
    # @return an integer
    def solve(self, A, B):
        n = len(A)

        curr_sum = 0
        min_len = n + 1
      
        start = 0
        end = 0
        while (end < n): 
            while (curr_sum < B and end < n): 
                curr_sum += A[end] 
                end+= 1
      
            while (curr_sum >= B and start < n): 
              
                if (end - start < min_len): 
                    min_len = end - start  
      
                curr_sum -= A[start] 
                start+= 1
          
        return min_len  if min_len != n+1 else -1
```