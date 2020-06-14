<h1>Sudoku</h1>

<p>
Write a program to solve a Sudoku puzzle by filling the empty cells.
Empty cells are indicated by the character '.'. You may assume that there will be only one unique solution.
<br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png">

A sudoku puzzle,
<br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/31/Sudoku-by-L2G-20050714_solution.svg/250px-Sudoku-by-L2G-20050714_solution.svg.png">

and its solution numbers marked in red.

Example :

For the above given diagrams, the corresponding input to your program will be

```
[[53..7....], [6..195...], [.98....6.], [8...6...3], [4..8.3..1], [7...2...6], [.6....28.], [...419..5], [....8..79]]
```
and we would expect your program to modify the above array of array of characters to

```
[[534678912], [672195348], [198342567], [859761423], [426853791], [713924856], [961537284], [287419635], [345286179]]
```
    
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of list of chars
    # @return nothing
    def has_empty_space(self,A,empty):
        for i in range(9):
            for j in range(9):
                if A[i][j] == ".":
                    empty[0],empty[1] = i,j
                    return True
                    
        return False
     
    def is_used_in_row(self,A,row,num):
        for i in range(9):
            if A[row][i] != '.' and int(A[row][i]) == num:
                return True
        return False
    
    def is_used_in_col(self,A,col,num):
        for i in range(9):
            if A[i][col] != '.' and int(A[i][col]) == num:
                return True
        return False
    
    def is_used_in_box(self,A,row,col,num):
        box_x = row // 3
        box_y = col // 3
    
        for i in range(box_x*3, box_x*3 + 3):
            for j in range(box_y * 3, box_y*3 + 3):
                if A[i][j] != '.' and int(A[i][j]) == num:
                    return True
        return False
        
    def check_if_is_safe(self,A,row,col,num):
        return not self.is_used_in_row(A,row, num) and not self.is_used_in_col(A,col, num) and not self.is_used_in_box(A,row,col, num)
        
    def solve_sudoku(self,A):
        
        empty = [0,0]
        
        if not self.has_empty_space(A,empty):
            return True
        
        row,col = empty
        
        for num in range(1,10):
            if self.check_if_is_safe(A,row,col,num):
                A[row][col] = str(num)
                
                if self.solve_sudoku(A):
                    return True
                    
                A[row][col] = "."
                
        return False
    def solveSudoku(self, A):
        # A = [list(i) for i in A]
    
        self.solve_sudoku(A)
```