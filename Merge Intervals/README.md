Merge Intervals
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
    vector<Interval> merge(vector<Interval>& intervals) {
        if(intervals.empty()) return {};
        
        sort(intervals.begin(), intervals.end(), 
            [](const Interval& a, const Interval& b) {
                return a.start < b.start;
            });
        
        int N = intervals.size();
        vector<Interval> result;
        Interval tmp;
        tmp = intervals[0];
        for(int i(1); i < N; ++i)
        {
            if(intervals[i].start <= tmp.end)
            {
                tmp.end = max(intervals[i].end, tmp.end);
            }
            else
            {
                result.push_back(tmp);
                tmp = intervals[i];
            }
        }
        result.push_back(tmp);
        return result;
    }
};
```
