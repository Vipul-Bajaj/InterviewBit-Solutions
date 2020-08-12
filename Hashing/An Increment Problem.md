<h1>An Increment Problem</h1>

<p>
Given a stream of numbers A. On arrival of each number, you need to increase its first occurence by 1 and include this in the stream.

Return the final stream of numbers.

Problem Constraints
    
    1 <= |A| <= 100000
    1 <= A[i] <= 10000
Input Format

    First and only argument is the array A.
Output Format

    Return an array, the final stream of numbers.
Example Input

    Input 1:
        A = [1,1]
    Input 2:
        A = [1,2]
    Output 1:
        [2,1]
    Output 2:
        [1,2]
    Explanation 1:
        On arrival of the second element, the other element is increased by 1.
    Explanation 2:
        No increases are to be done.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return a list of integers
    def solve(self, A):
        hash_map = {}
    
        for i in range(len(A)):
            if A[i] in hash_map:
                hash_map[A[i]+1] = hash_map[A[i]]
                A[hash_map[A[i]]] += 1
            hash_map[A[i]] = i
        
        return A
```