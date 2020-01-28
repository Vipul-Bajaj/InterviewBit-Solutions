<h1>Merge Intervals</h1>

<p>Given a set of non-overlapping intervals, insert a new interval into the intervals (merge if necessary).

You may assume that the intervals were initially sorted according to their start times.</p>

<p>
<b>Example 1:</b>
<br>
Given intervals [1,3],[6,9] insert and merge [2,5] would result in [1,5],[6,9].
<br>
<b>Example 2:</b>
<br>
Given [1,2],[3,5],[6,7],[8,10],[12,16], insert and merge [4,9] would result in [1,2],[3,10],[12,16].

This is because the new interval [4,9] overlaps with [3,5],[6,7],[8,10].
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
    # @param new_interval, a Interval
    # @return a list of Interval
    def insert(self, intervals, new_interval):
        start = newInterval.start
        end = newInterval.end
        right = left = 0
        while right < len(intervals):
            if start <= intervals[right].end:
                if end < intervals[right].start:
                    break
                start = min(start, intervals[right].start)
                end = max(end, intervals[right].end)
            else:
                left += 1
            right += 1
        return intervals[:left] + [Interval(start, end)] + intervals[right:]
```