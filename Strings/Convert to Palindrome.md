<h1>Convert to Palindrome</h1>

<p>
Given a string A consisting only of lowercase characters, we need to check whether it is possible to make this string a palindrome after removing exactly one character from this.

If it is possible then return 1 else return 0.

Problem Constraints

    3 <= |A| <= 10^5
    A[i] is always a lowercase character.
Input Format

    First and only argument is an string A.
Output Format
    
    Return 1 if it is possible to convert A to palindrome by removing exactly one character else return 0.

Example:

    Input 1:
        A = "abcba"
    Input 2:
        A = "abecbea"
    Output 1:
        1
    Output 2:
        0
    Explanation 1:
        We can remove character ‘c’ to make string palindrome
    Explanation 2:
        It is not possible to make this string palindrome just by removing one character

<h2>Solution</h2>

***

```python
def isPalindrome(A,i,j):
    s = A[i:j+1]
    if s == s[::-1]:
        return 1
    else:
        return 0
class Solution:
    # @param A : string
    # @return an integer
    def solve(self, A):
        n = len(A)
        i,j= 0,n-1
        
        while i<j:
            if A[i] != A[j]:
                if isPalindrome(A,i+1,j) or isPalindrome(A,i,j-1):
                    return 1
                else:
                    return 0
            i+=1
            j-=1
        return 1
```