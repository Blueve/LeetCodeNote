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
  Better, one pass, using bit to present 1-9's arrangement
  ```cpp
  class Solution {
  public:
      bool isValidSudoku(vector<vector<char>>& board) {
          short row[9] = {0}, col[9] = {0}, block[3][3] = {0};
          for(int i(0); i < 9; i++)
          {
              for(int j(0); j < 9; j++)
              {
                  short b = 1 << board[i][j] - '0';
                  if(row[i] & b || col[j] & b || block[i/3][j/3] & b) return false;
                  row[i] |= b;
                  col[j] |= b;
                  block[i/3][j/3] |= b;
              }
          }
          return true;
      }
  };
  ```