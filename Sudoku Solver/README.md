Sudoku Solver
==========

## C++


```cpp
class Solution {
public:
    void solveSudoku(vector<vector<char>>& board) {
        bool col[9][9] = {0}, row[9][9] = {0}, block[3][3][9] = {0};
        for(int i = 0; i < 9; ++i)
        {
            for(int j = 0; j < 9; ++j)
            {
                if(board[i][j] != '.')
                {
                    int n = board[i][j] - '1';
                    col[i][n] = row[j][n] = block[i / 3][j / 3][n] = true;
                }
            }
        }
        solve(board, col, row, block, 0);
    }
    
    bool solve(
        vector<vector<char>>& board,
        bool col[9][9],
        bool row[9][9],
        bool block[3][3][9],
        int id)
    {
        for(int i = id; i < 81; ++i)
        {
            int x = i / 9;
            int y = i % 9;
            if(board[x][y] == '.')
            {
                for(int n = 0; n < 9; ++n)
                {
                    // Conflict
                    if(col[x][n] || row[y][n] || block[x / 3][y / 3][n])
                        continue;
                    
                    // Try expend
                    board[x][y] = n + '1';
                    col[x][n] = row[y][n] = block[x / 3][y / 3][n] = true;
                    
                    if(solve(board, col, row, block, i + 1))
                        return true;
                    // Backtracing
                    board[x][y] = '.';
                    col[x][n] = row[y][n] = block[x / 3][y / 3][n] = false;
                }
                return false;
            }
        }
        return true;
    } 
};
```
