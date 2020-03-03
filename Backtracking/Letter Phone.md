<h1>Letter Phone</h1>

<p>
Given a digit string, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below.

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png">

The digit 0 maps to 0 itself.
The digit 1 maps to 1 itself.

    Input: Digit string "23"
    Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
Make sure the returned strings are lexicographically sorted.
    
</p>

<h2>Solution</h2>

***

```python
num_to_letter_map = {
    0:["0"],
    1:["1"],
    2:["a","b","c"],
    3:["d","e","f"],
    4:["g","h","i"],
    5:["j","k","l"],
    6:["m","n","o"],
    7:["p","q","r","s"],
    8:["t","u","v"],
    9:["w","x","y","z"]
}
def solve(A,res,st):
    if len(A) == 0:
        res.append("".join(st))
        return
    
    l = int(A[0])
    for j in num_to_letter_map[l]:
        st.append(j)
        solve(A[1:],res,st)
        st.pop(-1)
    
    return res
class Solution:
    # @param A : string
    # @return a list of strings
    def letterCombinations(self, A):
        A = list(str(A))
        return solve(A,[],[])
```