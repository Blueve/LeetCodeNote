Add Digits
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      int addDigits(int num) {
          if(!num) return 0;
          
          int tmp = num % 9;
          return tmp ? tmp : 9;
      }
  };
  ```