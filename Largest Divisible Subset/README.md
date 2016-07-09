Largest Divisible Subset
==========

## C++


```cpp
class Solution {
public:
    vector<int> largestDivisibleSubset(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        vector<int> path(nums.size()), DP(nums.size());
        int mi = 0, m = 0;
        
        for(int i = 0; i < nums.size(); ++i)
        {
            for(int j = i; j >= 0; --j)
            {
                if(nums[i] % nums[j] == 0 &&
                   DP[j] + 1 > DP[i])
                {
                    DP[i] = DP[j] + 1;
                    path[i] = j;
                }
            }
            if(DP[i] > m)
            {
                m = DP[i];
                mi = i;
            }
        }
        // Backtrace
        vector<int> result;
        while(m--)
        {
            result.push_back(nums[mi]);
            mi = path[mi];
        }
        reverse(result.begin(), result.end());
        return result;
    }
};
```
