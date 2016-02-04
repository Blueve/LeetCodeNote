Number of 1 Bits
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      int hammingWeight(uint32_t n) {
          int result(0);
          for(; n; n >>= 1)
              result += n & 1;
          return result;
      }
  };
  ```