Climbing Stairs
==========

## C++

  - Answer

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