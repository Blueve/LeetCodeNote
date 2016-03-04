House Robber
==========

## C++


```cpp
class Solution {
public:
    int rob(vector<int>& nums) {
        int N(nums.size()), tmp, max(0);
        
        if(!N) return 0;
        
        int *DP = new int[N] {0};
        //f(p) = nums[p] + max{num[i], i < p - 1}
        for(int p(0); p < N; ++p)
        {
            tmp = 0;
            for(int i(0); i < p - 1; ++i)
            {
                if(DP[i] > tmp) tmp = DP[i];
            }
            DP[p] = nums[p] + tmp;
            if(DP[p] > max) max = DP[p];
        }
        return max;
    }
};
```
Better
```cpp
class Solution {
public:
    int rob(vector<int>& nums) {
        int max(0), preMax(0);
        
        for(auto num : nums)
        {
            int cur = preMax + num;
            preMax = max;
            if(cur > max) max = cur;
        }
        return max;
    }
};
```
