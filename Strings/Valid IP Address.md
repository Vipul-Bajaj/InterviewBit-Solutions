<h1>Valid IP Address</h1>

<p>Given a string containing only digits, restore it by returning all possible valid IP address combinations.

A valid IP address must be in the form of A.B.C.D, where A,B,C and D are numbers from 0-255. The numbers cannot be 0 prefixed unless they are 0.
</p>

<p><b>Example :</b><br>Given “25525511135”,<br>return [“255.255.11.135”, “255.255.111.35”]. (Make sure the returned strings are sorted in order)</p>

<h2>Solution</h2>

***

```python
def is_valid(ip): 
  
    # Splitting by "." 
    ip = ip.split(".") 
      
    # Checking for the corner cases 
    for i in ip: 
        if len(i) > 3 or int(i) < 0 or int(i) > 255: 
            return False
        if len(i) > 1 and int(i) == 0: 
            return False
        if len(i) > 1 and int(i) != 0 and i[0] == '0': 
            return False
    return True
    
class Solution:
    # @param A : string
    # @return a list of strings
    def restoreIpAddresses(self, A):
        n = len(A)
        if n<4 or n>12:
            return []
        
        if n == 4:
            A = A[0:1] + "." + A[1:2] + "." + A[2:3] + "." + A[3:4]
            return [A]
            
        elif n == 12:
            p1 = A[:3]
            p2 = A[3:6]
            p3 = A[6:9]
            p4 = A[9:12]
            
            if int(p1)>255 or int(p2)>255 or int(p3)>255 or int(p4)>255:
                return []
            
            A = A[0:3] + "." + A[3:6] + "." + A[6:9] + "." + A[9:12]
            return [A]
            
        else:
            ans = []
            sz = len(A)
            snew = A
            for i in range(1, sz - 2): 
                for j in range(i + 1, sz - 1): 
                    for k in range(j + 1, sz): 
                        snew = snew[:k] + "." + snew[k:] 
                        snew = snew[:j] + "." + snew[j:] 
                        snew = snew[:i] + "." + snew[i:] 
                          
                        # Check for the validity of combination 
                        if is_valid(snew): 
                            ans.append(snew) 
                        snew = A
                        
            return sorted(ans)
```