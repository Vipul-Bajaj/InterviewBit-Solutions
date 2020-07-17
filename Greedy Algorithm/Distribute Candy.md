<h1>Distribute Candy</h1>

<p>
There are N children standing in a line. Each child is assigned a rating value.

You are giving candies to these children subjected to the following requirements:

1. Each child must have at least one candy.
2. Children with a higher rating get more candies than their neighbors.
What is the minimum candies you must give?

Input Format:
    
    The first and the only argument contains N integers in an array A.

Output Format:

    Return an integer, representing the minimum candies to be given.

Example:

    Input 1:
        A = [1, 2]

    Output 1:
        3

    Explanation 1:
        The candidate with 1 rating gets 1 candy and candidate with rating cannot get 1 candy as 1 is its neighbor. 
        So rating 2 candidate gets 2 candies. In total, 2 + 1 = 3 candies need to be given out.

    Input 2:
        A = [1, 5, 2, 1]

    Output 2:
        7

    Explanation 2:
        Candies given = [1, 3, 2, 1]

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return an integer
    def candy(self, A):
        n = len(A)
    
        candies = [1]*n
        
        for i in range(1,n):
            if A[i] == A[i-1]:
                continue
            elif A[i]>A[i-1] and candies[i]<=candies[i-1]:
                candies[i] = candies[i-1]+1
            else:
                j = i-1
                while j>=0  and A[j]>A[j+1] and candies[j]<=candies[j+1]:
                    candies[j]=candies[j+1]+1
                    j-=1
                    
        ans = candies[0]
        for i in range(1,n):
            ans+=candies[i]
        return ans
```