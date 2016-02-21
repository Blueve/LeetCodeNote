Excel Sheet Column Title
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      string convertToTitle(int n) {
          string result;
          while(n--)
          {
              result += n % 26 + 'A';
              n /= 26;
          }
          reverse(result.begin(), result.end());
          return result;
      }
  };
  ```