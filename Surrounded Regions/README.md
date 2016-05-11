Surrounded Regions
==========

## C++

BFS
```cpp
class Solution {
    int n, m;
public:
    void solve(vector<vector<char>>& board) {
        if(board.empty()) return;
        n = board.size();
        m = board[0].size();
        
        vector<vector<bool>> visit(n, vector<bool>(m));
        
        for(int i(0); i < n; ++i)
        {
            if(board[i][0] == 'O' && !visit[i][0])
                bfs(board, visit, i, 0);
            if(board[i][m - 1] == 'O' && !visit[i][m - 1])
                bfs(board, visit, i, m - 1);
        }
        for(int i(0); i < m; ++i)
        {
            if(board[0][i] == 'O' && !visit[0][i])
                bfs(board, visit, 0, i);
            if(board[n - 1][i] == 'O' && !visit[n - 1][i])
                bfs(board, visit, n - 1, i);
        }
        
        for(int i(0); i < n; ++i)
            for(int j(0); j < m; ++j)
                if(!visit[i][j]) board[i][j] = 'X';
    }
    
    void bfs(
        vector<vector<char>>& board,
        vector<vector<bool>>& visit,
        const int i, const int j)
    {
        queue<pair<int, int>> bfs;
        bfs.push(make_pair(i, j));
        while(!bfs.empty())
        {
            int l = bfs.size();
            while(l--)
            {
                auto p = bfs.front();
                bfs.pop();
                int x = p.first, y = p.second;
                
                if(visit[x][y] || board[x][y] != 'O') continue;
                visit[x][y] = true;
                
                if(x > 0) bfs.push(make_pair(x - 1, y));
                if(y > 0) bfs.push(make_pair(x, y - 1));
                if(x < n - 1) bfs.push(make_pair(x + 1, y));
                if(y < m - 1) bfs.push(make_pair(x, y + 1));
            }
        }
    }
};
```
