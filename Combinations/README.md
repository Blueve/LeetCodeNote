Combinations
==========

## C++


```cpp
class Solution {
public:
    vector<vector<int>> combine(int n, int k) {
        vector<vector<int>> result;
        vector<int> line;
        _combine(n + 1, k, result, line, 1);
        return result;
    }
    
    void _combine(int n, int k, vector<vector<int>>& result, vector<int>& line, int start)
    {
        if(k == 0)
        {
            result.push_back(line);
            return;
        }
        else
        {
            for(int i(start); i <= n - k && i <= n; ++i)
            {
                line.push_back(i);
                _combine(n, k - 1, result, line, i + 1);
                line.pop_back();
            }
        }
    }
};
```
