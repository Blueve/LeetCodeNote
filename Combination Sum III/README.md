Combination Sum III
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      vector<vector<int>> combinationSum3(int k, int n) {
          vector<vector<int>> result;
          vector<int> path;
          _combinationSum3(k, n, result, path, 1);
          return result;
      }
      
      void _combinationSum3(int k, int n, vector<vector<int>> &result, vector<int> &path, int   start)
      {
          if(n == 0 && k == 0)
          {
              result.push_back(path);
              return;
          }
          // e. If remain 3 numbers: [1 2 3 4 5 6 7]8 9
          // Cause number on the right must large than left,
          // then i start with current max number + 1.
          for(int i(start); i <= 10 - k && i <= n; ++i)
          {
              path.push_back(i);
              _combinationSum3(k - 1, n - i, result, path, i + 1);
              path.pop_back();
          }
      }
  };
  ```