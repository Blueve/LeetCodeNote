Number of Islands
==========

## C++


```cpp
class Solution {
public:
    int numIslands(vector<vector<char>>& grid) {
        int m(grid.size());
        if(!m) return 0;
        int n(grid[0].size()), count(0);
        vector<vector<bool>> visited(m, vector<bool>(n, false));
        for(int i(0); i < m; ++i)
        {
            for(int j(0); j < n; ++j)
            {
                if(!visited[i][j] && grid[i][j] == '1')
                {
                    dfs(grid, i, j, visited);
                    ++count;
                }
            }
        }
        return count;
    }
    
    void dfs(vector<vector<char>>& grid, int i, int j, vector<vector<bool>>& visited)
    {
        if(i < 0 || 
           j < 0 || 
           i == grid.size() || 
           j == grid[0].size() || 
           visited[i][j] ||
           grid[i][j] == '0') return;
           
        visited[i][j] = true;
        
        dfs(grid, i - 1, j, visited);
        dfs(grid, i, j - 1, visited);
        dfs(grid, i + 1, j, visited);
        dfs(grid, i, j + 1, visited);
    }
};
```
