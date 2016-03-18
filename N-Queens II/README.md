N-Queens II
==========

## C++


```cpp
class Solution {
public:
    int totalNQueens(int n) {
        vector<int> board(n);
        return dfs(board, n, 0);
    }
    
    int dfs(vector<int>& board, int n, int i)
    {
        if(i == n) return 1;
        int count(0), j;
        for(int p(0); p < n; ++p)
        {
            // Check place 'p'
            for(j = 0; j < i; ++j)
            {
                if(board[j] == p || 
                   board[j] - j == p - i || 
                   board[j] + j == p + i)
                    break;
            }
            if(j != i) continue;
            board[i] = p;
            count += dfs(board, n, i + 1);
        }
        return count;
    }
};
```
