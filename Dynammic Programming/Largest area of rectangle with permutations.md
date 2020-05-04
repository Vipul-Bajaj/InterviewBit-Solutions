<h1>Largest area of rectangle with permutations</h1>

<p>
Given a binary grid i.e. a 2D grid only consisting of 0’s and 1’s, find the area of the largest rectangle inside the grid such that all the cells inside the chosen rectangle should have 1 in them. You are allowed to permutate the columns matrix i.e. you can arrange each of the column in any order in the final grid. Please follow the below example for more clarity.

Lets say we are given a binary grid of 3 * 3 size.

1 0 1

0 1 0

1 0 0

At present we can see that max rectangle satisfying the criteria mentioned in the problem is of 1 * 1 = 1 area i.e either of the 4 cells which contain 1 in it. Now since we are allowed to permutate the columns of the given matrix, we can take column 1 and column 3 and make them neighbours. One of the possible configuration of the grid can be:

1 1 0

0 0 1

1 0 0

Now In this grid, first column is column 1, second column is column 3 and third column is column 2 from the original given grid. Now, we can see that if we calculate the max area rectangle, we get max area as 1 * 2 = 2 which is bigger than the earlier case. Hence 2 will be the answer in this case.

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of integers
    # @return an integer
    def solve(self, A):
        m = len(A)
        if m<1:
            return 0
        n = len(A[0])
        
        hist = [[0 for j in range(n)]for i in range(m)]
        
        for j in range(n):
            for i in range(m):
                if A[i][j]==1:
                    hist[i][j] = hist[i-1][j]+1
                    
        for i in range(m):
            hist[i].sort(reverse=True)
            
        max_area = 0
        for i in range(m):
            for j in range(n):
                max_area = max(max_area,(j+1)*hist[i][j])
                
        return max_area
```