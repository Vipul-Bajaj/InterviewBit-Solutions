<h1>Min Steps in InfiniteGrid</h1>

<p>You are in an infinite 2D grid where you can move in any of the 8 directions:</p>

```python
(x,y) to 
(x+1,y), 
(x-1,y), 
(x,y+1), 
(x,y-1), 
(x-1,y-1), 
(x+1,y+1), 
(x-1,y+1), 
(x+1,y-1)
```

<p>You are given a sequence of points and the order in which you need to cover the points. Give the minimum number of steps in which you can achieve it. You start from the first point.</p>

<p><b>Input :</b> Given two integer arrays A and B, where A[i] is x coordinate and B[i] is y coordinate of ith point respectively.</p>

<p><b>Output :</b> Return an Integer, i.e minimum number of steps.</p>

<p><b>Example :</b><br>Input : [(0, 0), (1, 1), (1, 2)]<br>Output : 2</p>

<p>
It takes 1 step to move from (0, 0) to (1, 1). It takes one more step to move from (1, 1) to (1, 2).
<br>
This question is intentionally left slightly vague. Clarify the question by trying out a few cases in the “See Expected Output” section.</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : list of integers
    # @return an integer
    def coverPoints(self, A, B):
        n = len(A)
        steps = 0
        for i in range(n-1):
            steps+=max(abs(A[i]-A[i+1]),abs(B[i]-B[i+1]))
            
        return steps
```