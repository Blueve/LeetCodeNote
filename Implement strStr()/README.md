Implement strStr()
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      int strStr(string haystack, string needle) {
          int la(haystack.size()), lb(needle.size()), p;
          if(lb > la) return -1;
          else if(!lb) return 0;
          for(int i(0); i + lb <= la; ++i)
          {
              for(p = 0; p < lb; ++p)
              {
                  if(haystack[i + p] != needle[p]) break;
              }
              if(p == lb) return i;
          }
          return -1;
      }
  };
  ```