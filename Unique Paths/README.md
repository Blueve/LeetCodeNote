Unique Paths
==========

## C++

  - Answer

  ```cpp
  class Solution {
      
  public:
      int uniquePaths(int m, int n) {
          vector<vector<int> > grid(m, vector<int> (n, 1));
          for(int i(1); i < m; ++i)
          {
              for(int j(1); j < n; ++j)
              {
                  grid[i][j] = grid[i - 1][j] + grid[i][j - 1];
              }
          }
          return grid[m - 1][n - 1];
      }
  };
  ```

  Better
  ```cpp
  class Solution {
      
  public:
      int uniquePaths(int m, int n) {
          if(m > n) uniquePaths(n, m);
          vector<int> grid(m, 1);
          for(int i(1); i < n; ++i)
          {
              for(int j(1); j < m; ++j)
              {
                  grid[j] += grid[j - 1];
              }
          }
          return grid[m - 1];
      }
  };
  ```