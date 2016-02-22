Power of Three
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      bool isPowerOfThree(int n) {
          if(n > 1)
          {
            while(n % 3 == 0)  /= 3;
          }
          return n == 1;
      }
  };
  ```
  Without using loop / recursion
  ```cpp
  class Solution {
  public:
      bool isPowerOfThree(int n) {
          return n > 0 && 1162261467 % n == 0;
      }
  };
  ```