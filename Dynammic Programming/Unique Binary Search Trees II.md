<h1>Unique Binary Search Trees II</h1>

<p>
Given an integer A, how many structurally unique BST’s (binary search trees) exist that can store values 1…A?

Input Format:

    The first and the only argument of input contains the integer, A.
Output Format:

    Return an integer, representing the answer asked in problem statement.
Constraints:

    1 <= A <= 18
Example:

    Input 1:
        A = 3

    Output 1:
        5

    Explanation 1:

        1         3     3      2      1
         \       /     /      / \      \
          3     2     1      1   3      2
         /     /       \                 \
        2     1         2                 3

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return an integer
    def numTrees(self, A):
        n = A
        if (n == 0 or n == 1): 
            return 1
  
        # Table to store results of subproblems 
        catalan = [0 for i in range(n + 1)] 
      
        # Initialize first two values in table 
        catalan[0] = 1
        catalan[1] = 1
      
        # Fill entries in catalan[] using recursive formula 
        for i in range(2, n + 1): 
            catalan[i] = 0
            for j in range(i): 
                catalan[i] = catalan[i] + catalan[j] * catalan[i-j-1] 
      
        # Return last entry 
        return catalan[n] 
```