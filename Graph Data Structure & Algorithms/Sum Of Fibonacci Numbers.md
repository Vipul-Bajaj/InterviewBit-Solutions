<h1>Sum Of Fibonacci Numbers</h1>

<p>
How many minimum numbers from fibonacci series are required such that sum of numbers should be equal to a given Number N?

    Note : repetition of number is allowed.

Example:

    N = 4
    Fibonacci numbers : 1 1 2 3 5 .... so on
    here 2 + 2 = 4 
    so minimum numbers will be 2 

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return an integer
    def fibsum(self, A):
        fib = [0,1]

        last_n = 1
        i=2
        while last_n <=A:
            last_n = fib[i-1]+fib[i-2]
            fib.append(last_n)
            i+=1
        
        count = 0
        i-=1
        while A>0:
            count += A // fib[i]  
            A %= fib[i]  
  
            i -= 1
            
        return count
```