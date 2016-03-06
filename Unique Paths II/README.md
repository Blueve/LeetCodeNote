Unique Paths II
==========

## C++


```cpp
class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        int m(obstacleGrid.size()), n(obstacleGrid[0].size());
        vector<int> DP(n, 0);
        DP[0] = obstacleGrid[0][0] ? 0 : 1;
        for(int i(0); i < m; ++i)
        {
            DP[0] &= !obstacleGrid[i][0];
            for(int j(1); j < n; ++j)
            {
                DP[j] = obstacleGrid[i][j] ? 0 : DP[j - 1] + DP[j];
            }
        }
        return DP.back();
    }
};
```
