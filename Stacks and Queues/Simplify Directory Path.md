<h1>Simplify Directory Path</h1>

<p>
Given a string A representing an absolute path for a file (Unix-style).

Return the string A after simplifying the absolute path.

Note:

1. Absolute path always begin with ’/’ ( root directory ).
2. Path will not have whitespace characters.</p>

<p><b>Example :</b>
<br>

```python
Input 1:
    A = "/home/"
Output 1:
    "/home"

Input 2:
    A = "/a/./b/../../c/"
Output 2:
    "/c"
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return a strings
    def simplifyPath(self, A):
        A = A.split("/")
    
        st = []
        n = len(A)
        for i in range(n):
            if A[i]=='.' or A[i]=='':
                continue
            elif A[i]=='..':
                if len(st)>0:
                    st.pop(-1)
            else:
                st.append(A[i])
                
        if len(st) == 0:
            return "/"
        else:
            return "/" + "/".join(st)
```