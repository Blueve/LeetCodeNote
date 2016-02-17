Count and Say
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      string countAndSay(int n) {
          string s("1"), tmp;
          while(n --> 1)
          {
              tmp.clear();
              int len(s.size()), i(0), count(0);
              while(i < len)
              {
                  count = 0;
                  char start(s[i]);
                  while(i < len && s[i] == start)
                      ++count, ++i;
  
                  tmp += to_string(count) + start;
              }
              s = tmp;
          }
          return s;
      }
  };
  ```