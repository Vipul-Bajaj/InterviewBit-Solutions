<h1>Merge Overlapping Intervals</h1>

<p>Given a collection of intervals, merge all overlapping intervals.

For example:

    Given [1,3],[2,6],[8,10],[15,18],

    return [1,6],[8,10],[15,18].

Make sure the returned intervals are sorted.
</p>

<p>Make sure the returned intervals are also sorted.</p>

<h2>Solution</h2>

***

```python
# Definition for an interval.
# class Interval:
#     def __init__(self, s=0, e=0):
#         self.start = s
#         self.end = e

class Solution:
    # @param intervals, a list of Intervals
    # @return a list of Interval
    def comp(self,interval):
        return interval.start
        
    def merge(self, intervals):
        intervals.sort(key=self.comp)
        n = len(intervals)
        if n<2:
            return intervals
        left,right = 0,1
        while right < n:
            if intervals[left].end >= intervals[right].start:
                intervals[left].start = min(intervals[left].start, intervals[right].start)
                intervals[left].end = max(intervals[left].end, intervals[right].end)
                del intervals[right]
                n-=1
            else:
                left += 1
                right += 1
        return intervals
```