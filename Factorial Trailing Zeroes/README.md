Factorial Trailing Zeroes
==========

## C++

  - Answer
  Every factor which suffix is '5' lead to a zero.
  ```cpp
  class Solution {
  public:
      int trailingZeroes(int n) {
          int result(0);
          for(long long i(5); i <= n; i *= 5)
          {
              result += n / i;
          }
          return result;
      }
  };
  ```