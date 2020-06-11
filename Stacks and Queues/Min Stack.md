<h1>Min Stack</h1>

<p>
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

    push(x) – Push element x onto stack.
    pop() – Removes the element on top of the stack.
    top() – Get the top element.
    getMin() – Retrieve the minimum element in the stack.
Note that all the operations have to be constant time operations.

Questions to ask the interviewer :

    Q: What should getMin() do on empty stack? 
    A: In this case, return -1.

    Q: What should pop do on empty stack? 
    A: In this case, nothing. 

    Q: What should top() do on empty stack?
    A: In this case, return -1
 
NOTE : If you are using your own declared global variables, make sure to clear them out in the constructor. 
</p>

<h2>Solution</h2>

***

```python
class MinStack:
    
    def __init__(self):
        self.minimum = float('inf')
        self.stack = []
        
    # @param x, an integer
    def push(self, x):
        if x <= self.minimum:
            self.stack.append(self.minimum)
            self.minimum = x
        self.stack.append(x)

    # @return nothing
    def pop(self):
        if not self.stack:
            pass
        else:
            t = self.stack[-1]
            self.stack.pop()
            if self.minimum == t:
                self.minimum = self.stack[-1]
                self.stack.pop()

    # @return an integer
    def top(self):
        if not self.stack:
            return -1
            
        return self.stack[-1]


    # @return an integer
    def getMin(self):
        if not self.stack:
            return -1
        return self.minimum
```