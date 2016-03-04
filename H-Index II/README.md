H-Index II
==========

## C++

O(N)
```cpp
class Solution {
public:
    int hIndex(vector<int>& citations) {
        int N(citations.size()), count(0), h(INT_MAX);
        for(int i(N - 1); i >= 0; --i, ++count)
        {
            if(citations[i] < h) h = citations[i];
            if(count >= h) return count;
        }
        return count;
    }
};
```

O(log(N))
```cpp
class Solution {
public:
    int hIndex(vector<int>& citations) {
        int N(citations.size());
        
        int l(0), r(N), m(0);
        while(l < r)
        {
            m = l + (r - l >> 1);
            if(citations[m] >= N - m) r = m;
            else l = m + 1;
        }
        return N - l;
    }
};
```
