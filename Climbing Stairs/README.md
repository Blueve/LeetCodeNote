Climbing Stairs
==========

## C++

  - Answer
  Faster when large invokes
  ```cpp
  class Solution {
  public:
      map<int, int> DP;
  
      int climbStairs(int n) {
          if(n == 1) return 1;
          if(n == 2) return 2;
          if(DP.count(n)) return DP[n];
          return DP[n] = climbStairs(n - 1) + climbStairs(n - 2);
      }
  };
  ```
  
  Faster when few invokes
  ```cpp
  class Solution {
  public:
      int climbStairs(int n) {
          if(n < 3) return n;
          int pre1(1), pre2(2), result(3);
          for(int i(2); i < n; i++)
          {
              result = pre1 + pre2;
              pre1 = pre2;
              pre2 = result;
          }
          return result;
      }
  };
  ```