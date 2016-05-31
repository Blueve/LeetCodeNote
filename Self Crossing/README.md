Self Crossing
==========

## C++


```cpp
class Solution {
public:
    bool isSelfCrossing(vector<int>& x) {
        int i = 2, n = x.size();
        // Find first Xi <= Xi-2
        while(i < n && x[i] > x[i - 2]) ++i;
        
        // Compare with Xi-2,
        // If Xi >= Xi-2, return true;
        // And checnk cross with Xi-5 and Xi-4.
        while(++i < n)
        {
            if(x[i] >= x[i - 2] ||
               i > 3 && x[i - 1] == x[i - 3] && x[i] + x[i - 4] >= x[i - 2] ||
               i > 4 && x[i - 2] >= x[i - 4] && x[i] + x[i - 4] >= x[i - 2] && x[i - 1] + x[i - 5] >= x[i - 3])
                return true;
        }
        return false;
    }
};
```
