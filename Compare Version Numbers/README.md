Compare Version Numbers
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      int compareVersion(string version1, string version2) {
          int v1, v2, l1(version1.size()), l2(version2.size());
          int i(0), j(0);
          while(i < l1 || j < l2)
          {
              v1 = v2 = 0;
              while(i < l1 && version1[i] != '.')
              {
                  v1 *= 10;
                  v1 += version1[i++] - '0';
              }
              while(j < l2 && version2[j] != '.')
              {
                  v2 *= 10;
                  v2 += version2[j++] - '0';
              }
              if(v1 > v2)      return 1;
              else if(v1 < v2) return -1;
              ++i, ++j;
          }
          
          return 0;
      }
  };
  ```