Longest Increasing Path in a Matrix
==========

## C++


```cpp
class Solution {
    int v[4][2] = {{0, -1}, {0, 1}, {-1, 0}, {1, 0}};
public:
    int longestIncreasingPath(vector<vector<int>>& matrix) {
        int m(matrix.size());
        if(!m) return 0;
        int n(matrix[0].size());
        
        vector<vector<int>> DP(m, vector<int>(n));
        vector<vector<bool>> visit(m, vector<bool>(n, false));
        int max(0);
        for(int i(0); i < m; ++i)
        {
            for(int j(0); j < n; ++j)
            {
                if(!visit[i][j])
                    _dfs(matrix, visit, DP, i, j, m, n, INT_MIN);
                if(DP[i][j] > max) max = DP[i][j];
            }
        }
        return max;
    }
    
    int _dfs(
        vector<vector<int>>& matrix, 
        vector<vector<bool>>& visit, 
        vector<vector<int>>& DP, int i, int j, int m, int n, int pre) {
        // Boundary check
        if(i < 0 || j < 0 || i == m || j == n) return 0;
        
        if(matrix[i][j] > pre)
        {
            if(visit[i][j]) return DP[i][j];
            
            visit[i][j] = true;
            int max(0), next;
            for(int k(0); k < 4; ++k)
            {
                next = _dfs(matrix, visit, DP, i + v[k][0], j + v[k][1], m, n, matrix[i][j]);
                if(next > max) max = next;
            }
            return DP[i][j] = max + 1;
        }
        else
        {
            return 0;
        }
    }
};
```

Without visit array
```cpp
class Solution {
    int v[4][2] = {{0, -1}, {0, 1}, {-1, 0}, {1, 0}};
public:
    int longestIncreasingPath(vector<vector<int>>& matrix) {
        int m(matrix.size());
        if(!m) return 0;
        int n(matrix[0].size());
        
        vector<vector<int>> DP(m, vector<int>(n));
        int max(0);
        for(int i(0); i < m; ++i)
        {
            for(int j(0); j < n; ++j)
            {
                _dfs(matrix, DP, i, j, m, n);
                if(DP[i][j] > max) max = DP[i][j];
            }
        }
        return max;
    }
    
    int _dfs(vector<vector<int>>& matrix, vector<vector<int>>& DP, int i, int j, int m, int n) {
        if(DP[i][j]) return DP[i][j];
        
        int max(1), next, x, y;
        for(int k(0); k < 4; ++k)
        {
            x = i + v[k][0];
            y = j + v[k][1];
            if(x < 0 || y < 0 || x == m || y == n || matrix[i][j] >= matrix[x][y]) continue;
            next = 1 + _dfs(matrix, DP, x, y, m, n);
            if(next > max) max = next;
        }
        return DP[i][j] = max;
    }
};
```
