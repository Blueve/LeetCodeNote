Subsets
==========

## C++


```cpp
class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        int N(nums.size()), K(1 << N);
        sort(nums.begin(), nums.end());
        vector<vector<int>> result(K);
        for(int i(1); i < K; ++i)
        {
            for(int j(0); j < N; ++j)
            {
                if((i >> j) & 1) result[i].push_back(nums[j]);
            }
        }
        return result;
    }
};
```
