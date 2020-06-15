<h1>Kth Permutation Sequence</h1>

<p>
The set [1,2,3,…,n] contains a total of n! unique permutations.

By listing and labeling all of the permutations in order,
We get the following sequence (ie, for n = 3 ) :

1. "123"
2. "132"
3. "213"
4. "231"
5. "312"
6. "321"

Given n and k, return the kth permutation sequence.

    For example, given n = 3, k = 4, ans = "231"

Good questions to ask the interviewer :
1. What if n is greater than 10. How should multiple digit numbers be represented in string?
In this case, just concatenate the number to the answer.
so if n = 11, k = 1, ans = "1234567891011" 
2. Whats the maximum value of n and k? In this case, k will be a positive integer thats less than INT_MAX. n is reasonable enough to make sure the answer does not bloat up a lot.
</p>

<h2>Solution</h2>

***

```python
def findFirstNumIndex(k, n) :
    if n == 1:
        return 0,0

    n-=1 

    n_partial_fact = n

    while (k >= n_partial_fact and n > 1):
        n_partial_fact = n_partial_fact * (n - 1)
        n-=1

    first_num_index = k // n_partial_fact

    k = k % n_partial_fact

    return k,first_num_index
	
class Solution:
    # @param A : integer
    # @param B : integer
    # @return a strings
    def getPermutation(self, A, B):
        n = A
        k = B
        ans = ""

    	s = []
    
    	for i in range(1,n+1):
    	    s.append(i)
    
    	k = k - 1
    
    	for i in range(n):
    	    k,index = findFirstNumIndex(k, n - i)
    	    ans += str(s[index])
    	    del s[index]
    
    	return ans
```