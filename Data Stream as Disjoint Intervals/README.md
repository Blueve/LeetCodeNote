Data Stream as Disjoint Intervals
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
class SummaryRanges {
    struct cmp {
        bool operator() (const Interval& lhs, const Interval& rhs)
        {
            return lhs.start < rhs.start;
        }
    };
    
    set<Interval, cmp> intervals;
    
public:
    /** Initialize your data structure here. */
    SummaryRanges() {
        
    }
    
    void addNum(int val) {
        Interval num(val, val);
        auto it = intervals.lower_bound(num);
        
        // Try merge with cur
        if(it != intervals.end())
        {
            if(it->start == val + 1)
            {
                num.end = it->end;
                it = intervals.erase(it);
            }
        }
        // Try merge with pre
        if(it != intervals.begin())
        {
            --it;
            if(it->end == val - 1)
            {
                num.start = it->start;
                it = intervals.erase(it);
            }
            else if(it->end >= val)
            {
                return;
            }
        }
        
        intervals.insert(num);
    }
    
    vector<Interval> getIntervals() {
        return vector<Interval>(intervals.begin(), intervals.end());
    }
};

/**
 * Your SummaryRanges object will be instantiated and called as such:
 * SummaryRanges obj = new SummaryRanges();
 * obj.addNum(val);
 * vector<Interval> param_2 = obj.getIntervals();
 */
```
