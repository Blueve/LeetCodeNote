Minimum Path Sum
==========

## C++


```cpp
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        int n = grid.size();
        if(!grid.size()) return 0;
        int m = grid[0].size();
        vector<vector<int>> DP(n + 1, vector<int>(m + 1, INT_MAX));
        DP[n][m - 1] = DP[n - 1][m] = 0;
        for(int i(n - 1); i >= 0; --i)
        {
            for(int j(m - 1); j >= 0; --j)
            {
                DP[i][j] = grid[i][j] + min(DP[i + 1][j], DP[i][j + 1]);
            }
        }
        return DP[0][0];
    }
};
```

```cpp
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        int n = grid.size();
        if(n == 0) return 0;
        int m = grid[0].size();
        
        vector<int> DP(n + 1, INT_MAX);
        DP[1] = 0;
        for(int i(0); i < m; ++i)
        {
            for(int j(0); j < n; ++j)
            {
                DP[j + 1] = grid[j][i] + min(DP[j + 1], DP[j]);
            }
        }
        return DP[n];
    }
};
```
