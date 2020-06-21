<h1>Another chocolate game</h1>

<p>
Scooby is a very good mathematics teacher and that is why his students like him. It’s Scooby’s birthday and so he decided to gift chocolates to his students.

Scooby has a total of A different students and he buys B different chocolates for them. He wants to make sure that
each student gets exactly one chocolate. He is interested in knowing the number of ways in which these chocolates can be
distributed to students. As the number of ways can be quite large, he is interested in knowing the number of ways modulo
109+7.

Constraints:

    Number of testcases T: 1<=T<=10000
    Number of students of Scooby: 1<=N<=100000
    Number of chocolates: 1<=M<=100000
Input:

    An integer A
    An integer B
Note:

1. Each student is different
2. Each chocolate is different
3. Each student should get exactly one chocolate
4. Your code will run against multiple test cases (The function in which you run your code will be called T times.)

Output:

    One integer corresponding to the number of ways of distributing the choclates modulo 1000000007.
    
Examples:

    Input:
    3 
    3
    Output:
    6
    Explanation:
        Let's say there are three students s1,s2 and s3 and there are three chocolates c1,c2 and c3.
        Following is the possible distribution:
        (s1=>c1,s2=>c2,s3=>c3)
        (s1=>c1,s2=>c3,s3=>c2)
        (s1=>c2,s2=>c1,s3=>c3)
        (s1=>c2,s2=>c3,s3=>c1)
        (s1=>c3,s2=>c1,s2=>c2)
        (s1=>c3,s2=>c2,s1=>c1) 
</p>

<h2>Solution</h2>

***

```python
mod = int(1e9+7)
factorial = [0]*100001
factorial[0] = 1
for i in range(1, 100001):
    factorial[i] = (factorial[i-1]*i)%mod
class Solution:
    # @param A : integer
    # @param B : integer
    # @return an integer
    
    def solve(self, A, B):
        if B<A:
            return 0
        b1 = factorial[B]%mod
        b2 = factorial[B-A]%mod
        inv = pow(b2, mod-2, mod)
        return (b1*inv)%mod
```