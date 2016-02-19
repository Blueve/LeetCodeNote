Longest Common Prefix
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      string longestCommonPrefix(vector<string>& strs) {
          int N(strs.size()), n;
          if(!N) return "";
          
          n = strs[0].size();
          for(int p(0); p < n ; ++p)
          {
              char ch = strs[0][p];
              for(int i(1); i < N; ++i)
              {
                  if(strs[i].size() == p || strs[i][p] != ch)
                      return strs[i].substr(0, p);
              }
          }
          return strs[0];
      }
  };
  ```