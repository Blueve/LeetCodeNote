Palindrome Number
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      bool isPalindrome(int x) {
          if(x < 0) return false;
          
          long long flip(0);
          int number(x);
          while(number)
          {
              flip *= 10;
              flip += number % 10;
              number /= 10;
          }
          return flip == x;
      }
  };
  ```