Spiral Matrix II
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      vector<vector<int>> generateMatrix(int n) {
          const int vec[4][2] = {{0, 1}, {1, 0}, {0, -1}, {-1, 0}};
          vector<vector<int>> m(n, vector<int>(n, 0));
          
          int N(n * n), x(0), y(0), v(0);
          for(int i(1); i <= N; ++i)
          {
              m[x][y] = i;
              x += vec[v][0];
              y += vec[v][1];
              
              if(x < 0 || y < 0 || x == n || y == n || m[x][y])
              {
                  x -= vec[v][0];
                  y -= vec[v][1];
                  v = v == 3 ? 0 : v + 1;
                  x += vec[v][0];
                  y += vec[v][1];
              }
          }
          return m;
      }
  };
  ```
  Whitout backtrace
  ```cpp
  class Solution {
  public:
      vector<vector<int>> generateMatrix(int n) {
          vector<vector<int>> m(n, vector<int>(n, 0));
          int count(1), N(n * n);
          int top(0), bottom(n - 1), left(0), right(n - 1);
          while(count <= N)
          {
              for(int i(left); i <= right; ++i)
                  m[top][i] = count++;
              ++top;
              
              for(int i(top); i <= bottom; ++i)
                  m[i][right] = count++;
              --right;
                  
              for(int i(right); i >= left; --i)
                  m[bottom][i] = count++;
              --bottom;
                  
              for(int i(bottom); i >= top; --i)
                  m[i][left] = count++;
              ++left;
          }
          return m;
      }
  };
  ```