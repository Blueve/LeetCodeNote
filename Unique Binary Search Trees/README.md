Single Number
==========

## C++

  - Answer

  Math
  ```cpp
  class Solution {
  public:
      int numTrees(int n) {
          long long result(1), N(n << 1);
          for(int i(1); i <= n; ++i)
          {
              result = result * (N - i + 1) / i;
          }
          return result / (n + 1);
      }
  };
  ```
  DP
  ```cpp
  class Solution {
  public:
      int numTrees(int n) {
          int DP[32] = {0};
          DP[0] = 1;
          DP[1] = 1;
          for(int i(2); i <= n; ++i)
          {
              for(int j(0); j < i; ++j)
              {
                  // (j) + (i - j - 1) == i - 1
                  // sum(left * right)
                  DP[i] += DP[j] * DP[i - j - 1];
              }
          }
          return DP[n];
      }
  };
  ```