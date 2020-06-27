<h1>Scores</h1>

<p>
You are playing a game called “Ball Throw”. Each throw has value of either 2 or 3 points.

1. A throw is worth 2 points if the throw distance is less than or equal to "D" meters.
2. A throw is worth 3 points if the throw distance is larger than "D" meters, where "D" is some non-negative integer.

There are 2 teams competing and you need to get the maximum advantage for your team i.e (the points of the first team minus the points of the second team) has to be maximum.

Choose some value of D that would do the task and tell the the scores for both team for that particular value of D.

Input

    The first argument is an array of length N (1 ≤ N ≤ 200000) - the number of throws of the first team. It contains array of N integer numbers — the distances of throws Ai (1 ≤ Ai ≤ 2000000000).

    The second argument is an array of length M (1 ≤ M ≤ 200000) - the number of throws of the second team. It contains array of M integer numbers — the distances of throws Bi (1 ≤ Bi ≤ 2000000000).
Output

    Return array of two elements "A" "B" where "A" is first team's score and "B" is second teams score with an optimal "D".  If there are several values of "D" which optimize "A-B", find the one in which "A" is maximum.
Examples

    Input
        1 2 3
        5 6
    Output
        9 6
    Example Explanation : We can keep D = 0. Team A will then score 3 points on each of their throws with final score as 9. Team B scores 6. The difference is then 3 which is the most optimal difference possible.

    Input
        6 7 8 9 10
        1 2 3 4 5
    Output
        15 10
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : list of integers
    # @return a list of integers
    def solve(self, A, B):
        mixed_ar = sorted(list(zip(A, [1] * len(A))) + list(zip(B, [2] * len(B))))
        max_diff = 0
        argmax = mixed_ar[-1][0]
        curr_diff_a_b = 0
        
        for i in range(len(mixed_ar)):
            if (~i == len(mixed_ar)-1 or mixed_ar[~i][0] != mixed_ar[~i+1][0]):
                if curr_diff_a_b >= max_diff:
                    max_diff = curr_diff_a_b
                    argmax = mixed_ar[~i][0]
            
            curr_diff_a_b += 1 if mixed_ar[~i][1] == 1 else -1

        if len(A) - len(B) >= max_diff:
            max_diff = len(A) - len(B)
            argmax = mixed_ar[0][0] - 1
        
        return [sum([2 if t <= argmax else 3 for t in A]), 
                sum([2 if t <= argmax else 3 for t in B])]
```