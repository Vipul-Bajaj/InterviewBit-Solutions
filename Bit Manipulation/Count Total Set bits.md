<h1>XOR-ing the Subarrays!</h1>

<p>
Given a positive integer A, the task is to count the total number of set bits in the binary representation of all the numbers from 1 to A.

Return the count modulo 10^9 + 7.

Problem Constraints

    1 <= A <= 10^9

Input Format:

    First and only argument is an integer array A.
Output Format:

    Return an integer denoting the ( Total number of set bits in the binary representation of all the numbers from 1 to A )modulo 10^9 + 7.

Example:

    Input 1:
        A = 3
    Input 2:
        A = 1
    Output 1:
        4
    Output 2:
        1
    Explanation 1:
        DECIMAL    BINARY  SET BIT COUNT
            1          01        1
            2          10        1
            3          11        2
        1 + 1 + 2 = 4 
        Answer = 4 % 1000000007 = 4
    Explanation 2:
        A = 1
        DECIMAL    BINARY  SET BIT COUNT
            1          01        1
        Answer = 1 % 1000000007 = 1

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return an integer
    def solve(self, A):
        A += 1;  

        powerOf2 = 2;  

        cnt = A // 2;  
 
        while (powerOf2 <= A) : 
      
            # Total count of pairs of 0s and 1s  
            totalPairs = A // powerOf2;  

            cnt += (totalPairs // 2) * powerOf2;  
      
            if (totalPairs & 1) : 
                cnt += (A % powerOf2) 
            else : 
                cnt += 0

            powerOf2 <<= 1;  
      
        # Return the result  
        return cnt % 1000000007
```