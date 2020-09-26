<h1>Shortest common superstring</h1>

<p>
Given a set of strings, A of length N.
Return the length of smallest string which has all the strings in the set as substring.

Problem Constraints

    1 <= N <= 18
    1 <= A[i] <= 100
Input Format

    The first and the only argument has an array of strings, A.
Output Format
    
    Return an integer representing the minimum possible length of the resulting string.
Example:

    Input 1:
        A = ["aaaa", "aa"]
    Output 1:
        4
    Explanation 1:
        Shortest string: "aaaa"

    Input 2:
        A = ["abcd", "cdef", "fgh", "de"]
    Output 2:
        8
    Explanation 2:
        Shortest string: "abcdefgh"
<h2>Solution</h2>

***

```python
class Solution:
    def join(self, s1, s2):
        i = 0
        best = 0
        n = len(s1)
        m = len(s2)

        for i in range(n):
            end1 = min(n, i + m)
            len2 = (end1 - i)
            if s1[i:end1] == s2[:len2]:
                best = max(best, len2)

            i += 1

        return s1 + s2[best:], best

    def help_join(self, A, cache):
        n = len(A)

        if n == 1:
            return A

        key = '_'.join(A)

        if key in cache:
            return cache[key]

        best_score = 0
        candidates = []

        for i in range(n):
            for j in range(i+1,n):
                s1 = A[i]
                s2 = A[j]

                join1, score1 = self.join(s1, s2)
                join2, score2 = self.join(s2, s1)

                p1 = (score1, i, j, join1)
                p2 = (score1, i, j, join2)

                if score1 > best_score:
                    candidates = [p1]
                    best_score = score1
                elif score1 == best_score:
                    candidates.append(p1)

                if score2 > best_score:
                    candidates = [p2]
                    best_score = score2
                elif score2 == best_score:
                    candidates.append(p2)

        if best_score == 0:
            choices = [''.join(A)]
        else:
            choices = []

            for _, i, j, joined in candidates:
                new_A = [] + A
                del new_A[j]
                del new_A[i]
                new_A.append(joined)
                new_A.sort()

                nxt = self.help_join(new_A, cache)
                choices = choices + nxt

        cache[key] = choices

        return choices
    # @param A : list of strings
    # @return an integer
    def solve(self, A):
        A = [a for a in A if len(a) > 0]
        A.sort()

        choices = self.help_join(A, {})
        choices.sort(key=lambda x:len(x))

        return len(choices[0])
```
