<h1>Possibility of finishing all courses given pre-requisites</h1>

<p>
There are a total of A courses you have to take, labeled from 1 to A.

Some courses may have prerequisites, for example to take course 2 you have to first take course 1, which is expressed as a pair: [1,2].

Given the total number of courses and a list of prerequisite pairs, is it possible for you to finish all courses?

Return 1 if it is possible to finish all the courses, or 0 if it is not possible to finish all the courses.

Input Format:

    The first argument of input contains an integer A, representing the number of courses.
    The second argument of input contains an integer array, B.
    The third argument of input contains an integer array, C.
Output Format:

    Return a boolean value:
        1 : If it is possible to complete all the courses.
        0 : If it is not possible to complete all the courses.
Constraints:

    1 <= A <= 6e4
    1 <= length(B) = length(C) <= 1e5
    1 <= B[i], C[i] <= A
Example:

    Input 1:
        A = 3
        B = [1, 2]
        C = [2, 3]

    Output 1:
        1

    Explanation 1:
        It is possible to complete the courses in the following order:
            1 -> 2 -> 3

    Input 2:
        A = 2
        B = [1, 2]
        C = [2, 1]

    Output 2:
        0

    Explanation 2:
        It is not possible to complete all the courses.

<h2>Solution</h2>

***

```python
def hasCycle(adj_dict,node,visited,recstack):
    visited[node] = True
    recstack[node] = True
    
    for neighbour in adj_dict[node]:
        if visited[neighbour] == False:
            if hasCycle(adj_dict,neighbour,visited,recstack):
                return True
        elif recstack[neighbour] == True:
            return True
    recstack[node] = False
    return False
    
class Solution:
    # @param A : integer
    # @param B : list of integers
    # @param C : list of integers
    # @return an integer
    def solve(self, A, B, C):
        visited = [False]*(A+1)
        recstack = [False]*(A+1)
        
        adj_dict = {}
        for i in range(1,A+1):
            adj_dict[i] = []
        for i in range(len(B)):
            adj_dict[B[i]].append(C[i])
                
        for node,neighbours in adj_dict.items():
            if visited[node] == False:
                if hasCycle(adj_dict,node,visited,recstack) == True:
                    return 0
        
        return 1
```