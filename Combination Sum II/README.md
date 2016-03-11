Combination Sum II
==========

## C++


```cpp
class Solution {
public:
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        vector<vector<int>> result;
        vector<int> comb;
        sort(candidates.begin(), candidates.end());
        _combination(candidates, target, result, comb, 0);
        return result;
    }
    
    void _combination(vector<int>& candidates, int target, vector<vector<int>>& result, vector<int>& comb, int start)
    {
        if(target == 0)
            result.push_back(comb);
        
        for(int i(start); i < candidates.size(); ++i)
        {
            if(candidates[i] > target || i > start && candidates[i] == candidates[i - 1]) continue;
            
            comb.push_back(candidates[i]);
            _combination(candidates, target - candidates[i], result, comb, i + 1);
            comb.pop_back();
        }
    }
};
```
