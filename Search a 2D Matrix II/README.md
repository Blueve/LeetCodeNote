Search a 2D Matrix II
==========

## C++

  - Answer
  O(Nlog(M)) Time
  ```cpp
  class Solution {
  public:
      bool searchMatrix(vector<vector<int>>& matrix, int target) {
          int n(matrix[0].size() - 1), l, r, m;
          for(auto& line : matrix)
          {
              if(target < line[0] || target > line[n]) continue;
              l = 0; r = n;
              while(l <= r)
              {
                  m = l + ((r - l) >> 1);
                  if     (target < line[m]) r = m - 1;
                  else if(target > line[m]) l = m + 1;
                  else return true;
              }
          }
          return false;
      }
  };
  ```

  O(N + M) Time
  ```cpp
  class Solution {
  public:
      bool searchMatrix(vector<vector<int>>& matrix, int target) {
          int m(matrix.size()), n(matrix[0].size());
          
          // From top right -> left bottom
          int i(0), j(n - 1);
          while(i < m && j >= 0)
          {
              if     (matrix[i][j] < target) ++i;
              else if(matrix[i][j] > target) --j;
              else return true;
          }
          return false;
      }
  };
  ```