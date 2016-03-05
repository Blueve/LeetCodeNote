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

```cpp
class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>> result;
        vector<int> comb;
        
        sort(nums.begin(), nums.end());
        _subsets(nums, 0, result, comb);
        
        return result;
    }
    
    void _subsets(vector<int>& nums, int start, vector<vector<int>>& result, vector<int>& comb) {
        result.push_back(comb);
        
        for(int i(start); i < nums.size(); ++i)
        {
            comb.push_back(nums[i]);
            _subsets(nums, i + 1, result, comb);
            comb.pop_back();
        }
    }
};
```