Word Search
==========

## C++


```cpp
class Solution {
public:
    bool exist(vector<vector<char>>& board, string word) {
        auto visit = board;
        for(int i(0); i < board.size(); ++i)
        {
            for(int j(0); j < board[0].size(); ++j)
            {
                if(dfs(board, visit, word, i, j, 0)) return true;
            }
        }
        return false;
    }
    
    bool dfs(vector<vector<char>>& board, vector<vector<char>>& visit, string& word, int i, int j, int step)
    {
        if(i < 0 || j < 0 || i == board.size() || j == board[0].size() || 
           !visit[i][j] || board[i][j] != word[step])
            return false;
        if(step == word.length() - 1)
            return true;
        visit[i][j] = 0;
        bool r=dfs(board, visit, word, i + 1, j, step + 1) ||
               dfs(board, visit, word, i, j + 1, step + 1) ||
               dfs(board, visit, word, i - 1, j, step + 1) ||
               dfs(board, visit, word, i, j - 1, step + 1);
        visit[i][j] = 1;
        return r;
    }
};
```
