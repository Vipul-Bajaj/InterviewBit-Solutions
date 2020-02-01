<h1>Hotel Bookings Possible</h1>

<p>A hotel manager has to process N advance bookings of rooms for the next season. His hotel has K rooms. Bookings contain an arrival date and a departure date. He wants to find out whether there are enough rooms in the hotel to satisfy the demand. Write a program that solves this problem in time O(N log N) .</p>

<p>
<b>Example 1:</b>
<br>
<b>Input :</b>

```python
Arrivals : [1 3 5]
Departures : [2 6 8]
K : 1
```
<br>
<b>Output :</b>

```python
0
```
<br>
</p>

<h2>Solution</h2>

***

```python
class Solution:
    # @param arrive : list of integers
    # @param depart : list of integers
    # @param K : integer
    # @return a boolean
    def hotel(self, arrive, depart, K):
        n = len(arrive)
        arrive.sort()
        depart.sort()
        guest = []
        for i in range(n):
            guest.append([arrive[i],1])
            guest.append([depart[i],0])
            
        guest.sort()
        curr_active, max_active = 0, 0
        n = len(guest)    
        for i in range(n):
            if guest[i][1] == 1:
                curr_active +=1
                max_active = max(max_active,curr_active)
            else:
                curr_active-=1
                
        if K >= max_active:
            return 1
        return 0  
```