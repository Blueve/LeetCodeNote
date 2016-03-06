Combination Sum
==========

## C++

DFS
```cpp
class Solution {
public:
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<vector<int>> result;
        vector<int> path;
        
        sort(candidates.begin(), candidates.end());
        
        _combinationSum(candidates, target, result, path, 0);
        return result;
    }
    
    void _combinationSum(vector<int>& candidates, int target, vector<vector<int>>& result, vector<int>& path, int start)
    {
        if(target == 0)
        {
            result.push_back(path);
            return;
        }
        
        for(int i(start); i < candidates.size() && target >= candidates[i]; ++i)
        {
            path.push_back(candidates[i]);
            _combinationSum(candidates, target - candidates[i], result, path, i);
            path.pop_back();
        }
    }
};
```
