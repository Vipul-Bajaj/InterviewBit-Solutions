<h1>XOR-ing the Subarrays!</h1>

<p>
Given an integer array A of size N.

You need to find the value obtained by XOR-ing the contiguous subarrays, followed by XOR-ing the values thus obtained. Determine and return this value.

For example, if A = [3, 4, 5] :

    | Subarray | Operation | Result |
    |----------|-----------|--------|
    | 3        | None      | 3      |
    | 4        | None      | 4      |
    | 5        | None      | 5      |
    | 3,4      | 3^4       | 7      |
    | 4,5      | 4^5       | 1      |
    | 3,4,5    | 3^4^5     | 2      |

Now we take the resultant values and XOR them together:

3 ⊕ 4 ⊕ 5 ⊕ 7 ⊕ 1⊕ 2 = 6 we will return 6.

Problem Constraints

    1 <= N <= 10^5
    1 <= A[i] <= 10^8

Input Format:

    First and only argument is an integer array A.
Output Format:

    Return a single integer denoting the value as described above.

Example:

    Input 1:
        A = [1, 2, 3]
    Input 2:
        A = [4, 5, 7, 5]
    Output 1:
        2
    Output 2:
        0
    Explanation 1:
        1 ⊕ 2 ⊕ 3 ⊕  (1 ⊕ 2 ) ⊕ (2 ⊕ 3) ⊕ (1 ⊕ 2 ⊕ 3) = 2
    Explanation 2:
        4 ⊕ 5 ⊕ 7 ⊕ 5 ⊕ (4 ⊕ 5) ⊕ (5 ⊕ 7) ⊕ (7 ⊕ 5) ⊕ (4 ⊕ 5 ⊕ 7) ⊕ (5 ⊕ 7 ⊕ 5) ⊕ (4 ⊕ 5 ⊕ 7 ⊕ 5) = 0

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def solve(self, A):
        ans = 0
        n = len(A)
        for i in range(n):
            c = (i+1)*(n-i)
            if c%2!=0:
                ans^=A[i]
                
        return ans
```