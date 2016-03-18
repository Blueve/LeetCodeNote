N-Queens
==========

## C++


```cpp
class Solution {
public:
    vector<vector<string>> solveNQueens(int n) {
        vector<vector<string>> result;
        vector<int> board(n);
        dfs(board, n, 0, result);
        return result;
    }
    
    void dfs(vector<int>& board, int n, int i, vector<vector<string>>& result)
    {
        if(i == n)
        {
            vector<string> sol(n, string(n, '.'));
            for(int p(0); p < n; ++p)
                sol[p][board[p]] = 'Q';
            result.push_back(sol);
        }
        int j;
        for(int p(0); p < n; ++p)
        {
            for(j = 0; j < i; ++j)
            {
                if(board[j] == p || 
                   board[j] - j == p - i || 
                   board[j] + j == p + i)
                    break;
            }
            if(j != i) continue;
            board[i] = p;
            dfs(board, n, i + 1, result);
        }
    }
};
```
