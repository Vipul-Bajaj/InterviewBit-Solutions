<h1>Atoi</h1>

<p>Implement atoi to convert a string to an integer.

<b>Example :</b>
<br>

```python
Input : "9 2704"
Output : 9
```

Note: There might be multiple corner cases here. Clarify all your doubts using “See Expected Output”.

```python
Questions: 
Q1. Does string contain whitespace characters before the number?
A. Yes 
Q2. Can the string have garbage characters after the number?
A. Yes. Ignore it. 
Q3. If no numeric character is found before encountering garbage characters, what should I do?
A. Return 0. 
Q4. What if the integer overflows?
A. Return INT_MAX if the number is positive, INT_MIN otherwise. 
```

<b>Warning : DO NOT USE LIBRARY FUNCTION FOR ATOI.</b><br>
If you do, we will disqualify your submission retroactively and give you penalty points.

</p>
<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return an integer
    def atoi(self, A):
        int_max = (2**31)-1
        int_min = (-2**31)
        n = len(A)
        i = 0
        while i<n:
            if ord(A[i])<48 or ord(A[i])>57:
                break
            else:
                i+=1
                
        A = A[:i]
        
        if A=='':
            return 0
        
        n = len(A)-1
        num = 0
        for i in A:
            num +=  (ord(i)-48)*(10**n)
            n-=1
            
        if num>int_max:
            return int_max
        elif num<int_min:
            return int_min
        return num

```