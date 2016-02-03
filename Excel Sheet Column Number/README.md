Excel Sheet Column Number
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      int titleToNumber(string s) {
          int result(0), len(s.size());
          for(int i(0); i < len; ++i)
          {
              result *= 26;
              result += s[i] - 'A' + 1;
          }
          return result;
      }
  };
  ```