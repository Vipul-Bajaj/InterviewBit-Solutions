<h1>First non-repeating character in a stream of characters</h1>

<p>
Given a string A denoting a stream of lowercase alphabets. You have to make new string B.

B is formed such that we have to find first non-repeating character each time a character is inserted to the stream and append it at the end to B. If no non-repeating character is found then append '#' at the end of B.

Problem Constraints

    1 <= length of the string <= 100000
Input Format

    The only argument given is string A
Output Format
    
    Return a string B after processing the stream of lowercase alphabets A

Example:

    Input 1:
        A = "abadbc"
    Input 2:
        A = "abcabc"
    Output 1:
        aabbdd
    Output 2:
        aaabc#
    Explanation 1:
        "a"      -   first non repeating character 'a'
        "ab"     -   first non repeating character 'a'
        "aba"    -   first non repeating character 'b'
        "abad"   -   first non repeating character 'b'
        "abadb"  -   first non repeating character 'd'
        "abadbc" -   first non repeating character 'd'
    Explanation 2:
        "a"      -   first non repeating character 'a'
        "ab"     -   first non repeating character 'a'
        "abc"    -   first non repeating character 'a'
        "abca"   -   first non repeating character 'b'
        "abcab"  -   first non repeating character 'c'
        "abcabc" -   no non repeating character so '#'

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return a strings
    def solve(self, A):
        q = []
        B = ""
        n = len(A)
        d = {}
        
        for i in range(n):
            if A[i] not in d:
                q.append(A[i])
                d[A[i]] = 1
            else:
                if A[i] in  q:
                    q.remove(A[i])
            
            if q:
                B+=q[0]
            else:
                B+="#"
        return B
```