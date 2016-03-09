Permutations II
==========

## C++


```cpp
class Solution {
public:
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        vector<vector<int>> result;
        
        _permute(nums, result, 0, nums.size() - 1);
        return result;
    }
    
    void _permute(vector<int>& nums, vector<vector<int>>& result, int start, int end)
    {
        if(start == end)
        {
            result.push_back(nums);
            return;
        }
        
        unordered_set<int> m;
        for(int i(start); i <= end; ++i)
        {
            if(m.count(nums[i])) continue;
            m.insert(nums[i]);
            
            swap(nums[start], nums[i]);
            _permute(nums, result, start + 1, end);
            swap(nums[start], nums[i]);
        }
    }
};
```
