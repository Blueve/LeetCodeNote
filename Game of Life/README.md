Game of Life
==========

## C++

  - Answer
  O(N) Space
  ```cpp
  class Solution {
  public:
      void gameOfLife(vector<vector<int>>& board) {
          int v[8][2] = {{-1, -1}, {0, -1}, {-1, 0}, {0, 1}, {1, 0}, {1, 1}, {-1, 1}, {1, -1}};
          int m(board.size()), n(board[0].size());
          auto pre = board;
          for(int i(0); i < m; ++i)
          {
              for(int j(0); j < n; ++j)
              {
                  int count = 0;
                  for(int p(0); p < 8; ++p)
                  {
                      int x = i + v[p][0];
                      int y = j + v[p][1];
                      if(x >= 0 && y >= 0 && x < m && y < n)
                      {
                          if(pre[x][y]) count++;
                      }
                  }
                  if(count < 2 || count > 3) board[i][j] = 0;
                  else if(count == 2) ;
                  else if(count == 3) board[i][j] = 1;
                  else board[i][j] = 0;
              }
          }
      }
  };
  ```
  O(1) Space, using second bit store next state
  ```cpp
  class Solution {
  public:
      void gameOfLife(vector<vector<int>>& board) {
          int v[8][2] = {{-1, -1}, {0, -1}, {-1, 0}, {0, 1}, {1, 0}, {1, 1}, {-1, 1}, {1, -1}};
          int m(board.size()), n(board[0].size());
          auto pre = board;
          for(int i(0); i < m; ++i)
          {
              for(int j(0); j < n; ++j)
              {
                  int count = 0;
                  for(int p(0); p < 8; ++p)
                  {
                      int x = i + v[p][0];
                      int y = j + v[p][1];
                      if(x >= 0 && y >= 0 && x < m && y < n)
                      {
                          if(pre[x][y]) count++;
                      }
                  }
                  if(count < 2 || count > 3) board[i][j] = 0;
                  else if(count == 2) ;
                  else if(count == 3) board[i][j] = 1;
                  else board[i][j] = 0;
              }
          }
      }
  };
  ```