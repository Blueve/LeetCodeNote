House Robber II
==========

## C++


```cpp
class Solution {
public:
    int rob(vector<int>& nums) {
        int N(nums.size()), preMax(0), m(0), m1;
        if(N < 1) return 0;
        
        // Rob first house
        for(int i(2); i < N - 1; ++i)
        {
            int cur = preMax + nums[i];
            preMax = m;
            if(cur > m) m = cur;
        }
        m1 = m + nums[0];
        // Not rob first house
        preMax = m = 0;
        for(int i(1); i < N; ++i)
        {
            int cur = preMax + nums[i];
            preMax = m;
            if(cur > m) m = cur;
        }
        return max(m, m1);
    }
};
```
