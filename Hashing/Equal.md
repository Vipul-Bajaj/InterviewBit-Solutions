<h1>Equal</h1>

<p>Given an array A of integers, find the index of values that satisfy A + B = C + D, where A,B,C & D are integers values in the array.

    Note
    1)  Return the indices `A1 B1 C1 D1`, so that 
        A[A1] + A[B1] = A[C1] + A[D1]
        A1 < B1, C1 < D1
        A1 < C1, B1 != D1, B1 != C1 

    2)  If there are more than one solutions, then return the tuple of values which are lexicographical smallest. 

        Assume we have two solutions
        S1 : A1 B1 C1 D1 ( these are values of indices int the array )  
        S2 : A2 B2 C2 D2

        S1 is lexicographically smaller than S2 iff
        A1 < A2 OR
        A1 = A2 AND B1 < B2 OR
        A1 = A2 AND B1 = B2 AND C1 < C2 OR 
        A1 = A2 AND B1 = B2 AND C1 = C2 AND D1 < D2
</p>

<p><b>Example :</b>
<br>

    Input: [3, 4, 7, 1, 2, 9, 8]
    Output: [0, 2, 3, 5] (O index)

If no solution is possible, return an empty list.
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : list of integers
    # @return a list of integers
    def equal(self, A):
        sum_hash = {}
        solutions = []
        n = len(A)
        
        for i in range(n):
            for j in range(i+1,n):
                _sum = A[i]+A[j]
                if _sum in sum_hash:
                    a1,b1,c1,d1 = sum_hash[_sum][0],sum_hash[_sum][1],i,j
                    if a1<b1 and a1<c1 and c1<d1 and b1!=c1 and b1!=d1:
                        solutions.append([a1,b1,c1,d1])
                else:
                    sum_hash[_sum] = [i,j]
        
        if solutions:
            solutions.sort(key=lambda x:(x[0],x[1],x[2],x[3]))
            return solutions[0]
        return []
```