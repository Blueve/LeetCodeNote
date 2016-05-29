Dungeon Game
==========

## C++


```cpp
class Solution {
    int n, m;
    
public:
    int calculateMinimumHP(vector<vector<int>>& dungeon) {
        if(dungeon.empty()) return 1;
        n = dungeon.size();
        m = dungeon[0].size();
        
        vector<vector<int>> DP(n, vector<int>(m, INT_MIN));
        int minPath = dfs(dungeon, 0, 0, DP);
        return minPath > 0 ? 1 : 1 - minPath;
    }
    
    int dfs(vector<vector<int>>& dungeon, int i, int j, vector<vector<int>>& DP)
    {
        // Boundary check
        if(i == n || j == m)
            return INT_MIN;
        
        if(DP[i][j] != INT_MIN)
            return DP[i][j];
        
        // Reach goal
        if(i == n - 1 && j == m - 1)
            return dungeon[i][j] > 0 ? 0 : dungeon[i][j];
        
        // Select min cost way (max(HP))
        int next = max(dfs(dungeon, i + 1, j, DP), dfs(dungeon, i, j + 1, DP));
        int cur = dungeon[i][j] + next;
        return DP[i][j] = (cur > 0 ? 0 : cur);
    }
};
```
