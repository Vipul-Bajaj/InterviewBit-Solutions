<h1>Arrange II</h1>

<p>
You are given a sequence of black and white horses, and a set of K stables numbered 1 to K. You have to accommodate the horses into the stables in such a way that the following conditions are satisfied:

    1. You fill the horses into the stables preserving the relative order of horses. For instance, you cannot put horse 1 into stable 2 and horse 2 into stable 1. You have to preserve the ordering of the horses.
    2. No stable should be empty and no horse should be left unaccommodated.
    3. Take the product (number of white horses * number of black horses) for each stable and take the sum of all these products. This value should be the minimum among all possible accommodation arrangements
Examples:

    Input: {WWWB} , K = 2
    Output: 0

    Explanation:
    We have 3 choices {W, WWB}, {WW, WB}, {WWW, B}
    for first choice we will get 1*0 + 2*1 = 2.
    for second choice we will get 2*0 + 1*1 = 1.
    for third choice we will get 3*0 + 0*1 = 0.

    Of the 3 choices, the third choice is the best option. 

<b>If a solution is not possible, then return -1</b>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : integer
    # @return an integer
    def arrange(self, A, B):
        n = len(A)
    
        if B==0 or n == 0:
            return -1
        if n<B:
            return -1
        if n == B:
            return 0
        
        dp = [[-1 for j in range(B)]for i in range(n)]
        
        bc=0
        wc=0
        for i in range(n):
            if A[i] == 'B':
                bc+=1
            else:
                wc+=1
            dp[i][0] = bc*wc
            
        for j in range(1,B):
            for i in range(n):
                wt=0
                bk=0
                dp[i][j]=2**31;
                for k in range(i,-1,-1):
                    if A[k]=='B':
                        bk+=1
                    else:
                        wt+=1
                    dp[i][j] = min(dp[i][j],bk*wt+(dp[k-1][j-1] if k-1>=0 else 0))
                    
        return dp[n-1][B-1]
```