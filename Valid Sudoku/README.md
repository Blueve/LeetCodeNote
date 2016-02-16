Valid Sudoku
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      bool isValidSudoku(vector<vector<char>>& board) {
          set<char> hash;
          // -
          for(int i(0); i < 9; ++i)
          {
              hash.clear();
              for(int j(0); j < 9; ++j)
              {
                  if(board[i][j] != '.')
                  {
                      if(hash.count(board[i][j])) return false;
                      else hash.insert(board[i][j]);
                  }
              }
          }
          // |
          for(int i(0); i < 9; ++i)
          {
              hash.clear();
              for(int j(0); j < 9; ++j)
              {
                  if(board[j][i] != '.')
                  {
                      if(hash.count(board[j][i])) return false;
                      else hash.insert(board[j][i]);
                  }
              }
          }
          // 3x3
          for(int i(0); i < 9; i += 3)
          {
              for(int j(0); j < 9; j += 3)
              {
                  hash.clear();
                  for(int x(0); x < 3; ++x)
                  {
                      for(int y(0); y < 3; ++y)
                      {
                          if(board[i + x][j + y] != '.')
                          {
                              if(hash.count(board[i + x][j + y])) return false;
                              else hash.insert(board[i + x][j + y]);
                          }
                      }
                  }
              }
          }
          return true;
      }
  };
  ```