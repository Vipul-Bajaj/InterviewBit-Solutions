<h1>Two out of Three</h1>

<p>
Given are Three arrays A, B and C.
Return the sorted list of numbers that are present in atleast 2 out of the 3 arrays.

Problem Constraints

    1 <= |A|, |B|, |C| <= 100000
    1 <= A[i], B[i], C[i] <= 100000
    A, B, C may or may not have pairwise distinct elements.

Input Format

    First argument is the array A.
    First argument is the array B.
    First argument is the array C.

Output Format

    Return a sorted array of numbers.

Example Input

    Input 1:
        A = [1, 1, 2]
        B = [2, 3]
        C = [3]
    Input 2:
        A = [1, 2]
        B = [1, 3]
        C = [2, 3]

    Output 1:
        [2, 3]
    Output 2:
        [1, 2, 3]

    Explanation 1:
        1 is only present in A. 2 is present in A and B. 3 is present in B and C.
    Explanation 2:
        All numbers are present in atleast 2 out of 3 lists.`
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @param B : list of integers
    # @param C : list of integers
    # @return a list of integers
    def solve(self, A, B, C):
        hash_map = {}
    
        for i in A:
            if i in hash_map:
                hash_map[i].add('A')
            else:
                hash_map[i] = set(['A'])
        
        for i in B:
            if i in hash_map:
                hash_map[i].add('B')
            else:
                hash_map[i] = set(['B'])
                
        for i in C:
            if i in hash_map:
                hash_map[i].add('C')
            else:
                hash_map[i] = set(['C'])
        
        ans = []      
        for key in hash_map.keys():
            if len(hash_map[key])>=2:
                ans.append(key)
            
        return sorted(ans)
```