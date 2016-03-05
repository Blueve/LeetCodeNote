Subsets II
==========

## C++


```cpp
class Solution {
public:
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        vector<vector<int>> result;
        vector<int> comb;
        
        sort(nums.begin(), nums.end());
        _subsetsWithDup(nums, 0, result, comb);
        
        return result;
    }
    
    void _subsetsWithDup(vector<int>& nums, int start, vector<vector<int>>& result, vector<int>& comb) {
        result.push_back(comb);
        
        for(int i(start); i < nums.size(); ++i)
        {
            if(i > start && nums[i] == nums[i - 1]) continue;
            comb.push_back(nums[i]);
            _subsetsWithDup(nums, i + 1, result, comb);
            comb.pop_back();
        }
    }
};
```
