Find Median from Data Stream
==========

## C++


```cpp
class MedianFinder {
    priority_queue<int, vector<int>, less<int>> l;
    priority_queue<int, vector<int>, greater<int>> r;
public:

    // Adds a number into the data structure.
    void addNum(int num) {
        if(l.empty() || num <= l.top())
            l.push(num);
        else
            r.push(num);
        auto nl = l.size(), nr = r.size();
        if(nr > nl)
        {
            l.push(r.top());
            r.pop();
        }
        else if(nl > nr + 1)
        {
            r.push(l.top());
            l.pop();
        }
    }

    // Returns the median of current data stream
    double findMedian() {
        return l.size() > r.size() 
                ? l.top() 
                : ((double)l.top() + r.top()) / 2;
    }
};

// Your MedianFinder object will be instantiated and called as such:
// MedianFinder mf;
// mf.addNum(1);
// mf.findMedian();
```
