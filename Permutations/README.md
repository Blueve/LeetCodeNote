Permutations
==========

## C++


```cpp
class Solution {
public:
    vector<vector<int>> permute(vector<int>& nums) {
        vector<vector<int>> result;
        _permute(0, nums.size() - 1, nums, result);
        return result;
    }
    
    void _permute(int start, int end, vector<int>& nums, vector<vector<int>>& result)
    {
        if(start == end)
            result.push_back(nums);
        
        for(int i(start); i <= end; ++i)
        {
            //sort(nums.begin() + start, nums.end()); // For dict order
            swap(nums[start], nums[i]);
            _permute(start + 1, end, nums, result);
            swap(nums[start], nums[i]);
        }
    }
};
```
