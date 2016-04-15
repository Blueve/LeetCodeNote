Burst Balloons
==========

## C++


```cpp
class Solution {
public:
    int maxCoins(vector<int>& nums) {
        // Handle boundary
        vector<int> num = {1};
        for(auto i : nums) num.push_back(i);
        num.push_back(1);
        
        auto n = num.size();
        
        // DP[left][right] = maxCoins((left, right))
        vector<vector<int>> DP(n, vector<int>(n));
        
        // Pick i\left\right, the interval between left and right
        // will getting increase.
        for(int interval(2); interval < n; ++interval)
        {
            for(int l(0); l < n - interval; ++l)
            {
                int r = l + interval;
                for(int i(l + 1); i < r; ++i)
                {
                    DP[l][r] = max(DP[l][r], 
                                   DP[l][i] + DP[i][r] + num[l] * num[i] * num[r]);
                }
            }
        }
        
        return DP[0][n - 1];
    }
};
```
