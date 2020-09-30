<h1>Tushar's Birthday Party</h1>

<p>
As it is Tushar’s Birthday on March 1st, he decided to throw a party to all his friends at TGI Fridays in Pune.
Given are the eating capacity of each friend, filling capacity of each dish and cost of each dish. A friend is satisfied if the sum of the filling capacity of dishes he ate is equal to his capacity. Find the minimum cost such that all of Tushar’s friends are satisfied (reached their eating capacity).

NOTE:

1. Each dish is supposed to be eaten by only one person. Sharing is not allowed.
2. Each friend can take any dish unlimited number of times.
3. There always exists a dish with filling capacity 1 so that a solution always exists.

Problem Constraints:

    1 <= Capacity of friend <= 1000
    1 <= No. of friends <= 1000
    1 <= No. of dishes <= 1000
Input Format:

    Friends : List of integers denoting eating capacity of friends separated by space.
    Capacity: List of integers denoting filling capacity of each type of dish.
    Cost :    List of integers denoting cost of each type of dish.

Example:

    Input:
        2 4 6
        2 1 3
        2 5 3
    Output:
        14
    Explanation: 
        First friend will take 1st and 2nd dish, second friend will take 2nd dish twice.  Thus, total cost = (5+3)+(3*2)= 14

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : tuple of integers
    # @param B : tuple of integers
    # @param C : tuple of integers
    # @return an integer
    def solve(self, A, B, C):
        memo = [0] * (max(A) + 1)
        for i in range(1, max(A) + 1):
            memo[i] = min( memo[i-B[d]] + C[d] for d in range(len(B)) if i - B[d] >= 0 )
        return sum(memo[i] for i in A)
```
