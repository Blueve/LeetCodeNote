Roman to Integer
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      int romanToInt(string s) {
          int TB[87];
          TB['I'] = 1;
          TB['V'] = 5;
          TB['X'] = 10;
          TB['L'] = 50;
          TB['C'] = 100;
          TB['D'] = 500;
          TB['M'] = 1000;
          int result(0), len(s.length());
          
          for(int i(0); i < len; ++i)
          {
              if(i + 1 < len && TB[s[i]] < TB[s[i + 1]])
                  result -= TB[s[i]];
              else
                  result += TB[s[i]];
          }
          return result;
      }
  };
  ```