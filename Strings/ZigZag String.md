<h1>ZigZag String</h1>

<p>The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
</p>

```python
P.......A........H.......N
..A..P....L....S....I...I....G
....Y.........I........R
```

<p>
And then read line by line: PAHNAPLSIIGYIR
Write the code that will take a string and make this conversion given a number of rows:
</p>

```python
string convert(string text, int nRows);
convert("PAYPALISHIRING", 3) should return "PAHNAPLSIIGYIR"
```

<p><b>Example :</b><br>Input :<br>A = "PAYPALISHIRING" B = 3<br>Output :<br> "PAHNAPLSIIGYIR"</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @param B : integer
    # @return a strings
    def convert(self, A, B):
        n = B
        s = ["" for j in range(n)]
        j = 0
        cycle = "pos"
        for i in A:
            s[j]+=i
            if cycle == 'pos':
                if j == n-1:
                    cycle = 'neg'
                    j-=1
                    if j<0:
                        j=0
                else:
                    j+=1
            elif cycle == 'neg':
                if j == 0:
                    cycle = 'pos'
                    j+=1
                    if j>n-1:
                        j=n-1
                else:
                    j-=1
                    
        return "".join([x for x in s])
```