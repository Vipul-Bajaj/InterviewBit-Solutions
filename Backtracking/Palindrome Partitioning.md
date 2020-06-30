<h1>Palindrome Partitioning</h1>

<p>
Given a string s, partition s such that every string of the partition is a palindrome.

Return all possible palindrome partitioning of s.

For example, given s = "aab",
Return

    [
        ["a","a","b"]
        ["aa","b"],
    ]
Ordering the results in the answer : Entry i will come before Entry j if :
1. len(Entryi[0]) < len(Entryj[0]) OR
2. (len(Entryi[0]) == len(Entryj[0]) AND len(Entryi[1]) < len(Entryj[1])) OR
*
*
*
3. (len(Entryi[0]) == len(Entryj[0]) AND … len(Entryi[k] < len(Entryj[k]))

In the given example,
["a", "a", "b"] comes before ["aa", "b"] because len("a") < len("aa")
</p>

<h2>Solution</h2>

***

```python
def isPalindrome(a):
    b = a[::-1]
    if a == b:
        return True
    return False

def solveUtil(A, ans, current_ele, idx, n):
    if idx >= n: 
        c = current_ele[::]
        ans.append(c) 
        return
        
    for i in range(idx, n): 
        s = A[idx:i+1]
        if isPalindrome(s):
            current_ele.append(s)
            solveUtil(A, ans, current_ele, i + 1, n) 
            current_ele.pop()
            
class Solution:
    # @param A : string
    # @return a list of list of strings
    def partition(self, A):
        ans = []
        current_ele = []
        solveUtil(A, ans, current_ele, 0, len(A))
        return ans
```