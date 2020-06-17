<h1>The square game</h1>

<p>
You are given a square with sides parallel to the x and y axes.

You will be given the coordinates of the lower left and the
upper right vertices of the square. You need to count the number of integral points that are strictly inside the square.
The points that lie on the square should not be counted.

Image for sample case:

<img src="https://s3-us-west-2.amazonaws.com/ib-assessment-tests/problem_images/square.png">

Constraints:

    1 <= A, B, C, D <= 1000
    A != C
Input:

    An integer A corresponding to the x coordinate of the lower left vertex.
    An integer B corresponding to the y coordinate of the lower left vertex. 
    An integer C corresponding to the x coordinate of the upper right vertex.
    An integer D corresponding to the y coordinate of the upper right vertex.
Output:

    One integer corresponding to the number of integral points strictly inside the given square.
Examples:

    Input:

    1
    1
    4
    4

    Output:

    4
Explanation:

    (2,3),(3,2),(2,2),(3,3) are the integral points that are strictly inside the given square. Refer the diagram given in the given question for more details.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @param B : integer
    # @param C : integer
    # @param D : integer
    # @return an integer
    def solve(self, A, B, C, D):
        n = C-A
        return (n-1)**2
```