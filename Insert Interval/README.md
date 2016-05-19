Insert Interval
==========

## C++


```cpp
/**
 * Definition for an interval.
 * struct Interval {
 *     int start;
 *     int end;
 *     Interval() : start(0), end(0) {}
 *     Interval(int s, int e) : start(s), end(e) {}
 * };
 */
class Solution {
public:
    vector<Interval> insert(vector<Interval>& intervals, Interval newInterval) {
        vector<Interval> result;
        int i = 0, n = intervals.size();
        // Find insert point
        while(i < n)
        {
            if(newInterval.start <= intervals[i].start)
                break;
            else if(newInterval.start <= intervals[i].end)
            {
                newInterval.start = intervals[i].start;
                break;
            }
            result.push_back(intervals[i++]);
        }
        
        // Expend newInterval
        while(i < n)
        {
            if(newInterval.end > intervals[i].end)
                ++i;
            else if(newInterval.end >= intervals[i].start)
            {
                newInterval.end = intervals[i++].end;
                break;
            }
            else break;
        }
        result.push_back(newInterval);
        
        // Insert others
        while(i < n)
            result.push_back(intervals[i++]);
        
        return result;
    }
};
```
