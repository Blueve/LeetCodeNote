Palindrome Number
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      bool isPalindrome(int x) {
          // 10\100\... should return false
          if(x < 0 || (x % 10 == 0) && (x != 0)) return false;
          
          int flip(0);
          while(x > flip)
          {
              flip *= 10;
              flip += x % 10;
              x /= 10;
          }
          // Even / Odd
          return flip == x || flip / 10 == x;
      }
  };
  ```