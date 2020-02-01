<h1>Pretty JSON</h1>

<p>
Given a string A representating json object. Return an array of string denoting json object with proper indentaion.

Rules for proper indentaion:

    1. Every inner brace should increase one indentation to the following lines.
    2. Every close brace should decrease one indentation to the same line and the following lines.
    3. The indents can be increased with an additional ‘\t’
Note:

    1. [] and {} are only acceptable braces in this case.
    2. Assume for this problem that space characters can be done away with.
</p>

<p><b>For Example :</b>
<br>

```python
Input 1:
    A = "{A:"B",C:{D:"E",F:{G:"H",I:"J"}}}"
Output 1:
    { 
        A:"B",
        C: 
        { 
            D:"E",
            F: 
            { 
                G:"H",
                I:"J"
            } 
        } 
    }

Input 2:
    A = ["foo", {"bar":["baz",null,1.0,2]}]
Output 2:
   [
        "foo", 
        {
            "bar":
            [
                "baz", 
                null, 
                1.0, 
                2
            ]
        }
    ]
```
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param A : string
    # @return a list of strings
    def prettyJSON(self, A):
        curr_indent = ""
        res = []
        curr = ""
        for i,c in enumerate(A):
            if c == "[" or c == "{":
                if curr: 
                    res.append(curr_indent + curr)
                curr = curr_indent + c
                res.append(curr)
                curr_indent += "\t"
                curr = ""
            elif c == "]" or c == "}":
                if curr: 
                    res.append(curr_indent + curr)
                curr_indent = curr_indent[:-1]
                curr = curr_indent + c
                res.append(curr)
                curr = ""
            elif c == " ":
                curr = ""
            elif c == ",":
                if A[i-1] == "}" or A[i-1] == "]":
                    res[-1] = res[-1] + c
                else:
                    curr = curr_indent + curr + c
                    res.append(curr)
                    curr = ""
            else:
                curr += c

        return res
```