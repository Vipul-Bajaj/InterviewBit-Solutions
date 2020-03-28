<h1>FizzBuzz</h1>

<p>

    Fizzbuzz is one of the most basic problems in the coding interview world. Try to write a small and elegant code for this problem. 

Given a positive integer A, return an array of strings with all the integers from 1 to N.
But for multiples of 3 the array should have “Fizz” instead of the number.
For the multiples of 5, the array should have “Buzz” instead of the number.
For numbers which are multiple of 3 and 5 both, the array should have “FizzBuzz” instead of the number.

Look at the example for more details.
</p>

<p>
<b>Example :</b>
<br>

    A = 5
    Return: [1 2 Fizz 4 Buzz]
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : integer
    # @return a list of strings
    def fizzBuzz(self, A):
        res = [i+1 for i in range(A)]
        for i in range(A):
            if (i+1)%3==0 and (i+1)%5==0:
                res[i] = "FizzBuzz"
            elif (i+1)%5==0:
                res[i] = "Buzz"
            elif (i+1)%3==0:
                res[i] = "Fizz"
            else:
                continue
            
        return res
```