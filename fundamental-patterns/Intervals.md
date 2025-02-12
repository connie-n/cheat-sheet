## Intervals

## 🃏 Leetcode

- [Merge Intervals](https://leetcode.com/problems/merge-intervals/)
```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        intervals.sort(key=lambda x: x[0])
        merged = []

        for i in intervals:
            if merged and merged[-1][1] >= i[0]:
                merged[-1][1] = max(merged[-1][1], i[1])
            else:
                merged.append(i)
        return merged
```

- [Insert Interval](https://leetcode.com/problems/insert-interval/description/)
```python
class Solution:
    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        inserted = []
        
        for i in intervals:
            if i[1] < newInterval[0]:
                inserted.append(i)
  
            elif i[0] > newInterval[1]:
                inserted.append(newInterval)
                newInterval = i
            
            else:
                newInterval[0] = min(newInterval[0], i[0])
                newInterval[1] = max(newInterval[1], i[1])
        
        inserted.append(newInterval)
        return inserted
```

- [Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)
```python
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        intervals.sort(key=lambda x: x[1])
        removal = 0
        prev_end = float('-inf')

        for start, end in intervals:
            if start < prev_end:
                removal += 1
            else:
                prev_end = end
        
        return removal
```