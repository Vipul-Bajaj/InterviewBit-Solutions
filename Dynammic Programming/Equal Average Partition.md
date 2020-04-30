<h1>Equal Average Partition</h1>

<p>
Given an array with non negative numbers, divide the array into two parts such that the average of both the parts is equal.
Return both parts (If exist).
If there is no solution. return an empty list.

Example:

    Input:
        [1 7 15 29 11 9]

    Output:
        [9 15] [1 7 11 29]

    The average of part is (15+9)/2 = 12,
    average of second part elements is (1 + 7 + 11 + 29) / 4 = 12

<strong>NOTE 1:</strong> If a solution exists, you should return a list of exactly 2 lists of integers A and B which follow the following condition :
numElements in A <= numElements in B
If numElements in A = numElements in B, then A is lexicographically smaller than B ( https://en.wikipedia.org/wiki/Lexicographical_order )
<strong>NOTE 2:</strong> If multiple solutions exist, return the solution where length(A) is minimum. If there is still a tie, return the one where A is lexicographically smallest. 
<strong>NOTE 3:</strong> Array will contain only non negative numbers. 
<h2>Solution</h2>

***

```python
def possible(dp,array,res,index,curr_sum,curr_size):
    if (curr_size == 0) :
        return (curr_sum == 0)
    if (index >= len(array)) :
        return False; 
    if (dp[index][curr_sum][curr_size] == False) :
        return False; 
  
    if (curr_sum >= array[index]): 
        res.append(array[index])
        if possible(dp,array,res,index + 1, curr_sum -  array[index], curr_size - 1):
            return True; 
  
        res.pop(); 
        
    if possible(dp,array,res,index + 1, curr_sum, curr_size):
        return True; 
  
    dp[index][curr_sum][curr_size] = False
    
    return dp[index][curr_sum][curr_size]
class Solution:
    # @param A : list of integers
    # @return a list of list of integers
    def avgset(self, A):
        A.sort()
        n = len(A)
        s = sum(A)
        
        dp = [[[True for k in range(n)]for j in range(s+1)]for i in range(n)]
        
        for i in range(n+1):
            dp[0][i][0] = 1
        res = []    
        for i in range(1,n):
            if (s * i) % n != 0:
                continue
            sum_of_set1 = (s * i) // n
            
            if possible(dp,A,res,0, sum_of_set1, i):
      
                ptr1 = 0
                ptr2 = 0
                res1 = res; 
                res2 = []
                while (ptr1 < n or ptr2 < len(res)) :
                    if ptr2 < len(res) and res[ptr2] == A[ptr1]: 
                        ptr1+=1
                        ptr2+=1
                        continue
                    res2.append(A[ptr1])
                    ptr1+=1
      
                return [res1,res2]
                
        return [] 
```