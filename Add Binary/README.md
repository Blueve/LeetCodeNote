Add Binary
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      string addBinary(string a, string b) {
          
          if(b.size() > a.size()) swap(a, b);
          int la(a.size()), lb(b.size());
          
          for(int i(la - 1); i >= 0; --i)
          {
              if(i - (la - lb) >= 0)
                  a[i] += b[i - (la - lb)] - '0';
              if(a[i] > '1')
              {
                  a[i] = a[i] - 2;
                  if(i == 0) a = '1' + a;
                  else a[i - 1] += 1;
              }
          }
          return a;
      }
  };
  ```

  ```cpp
  class Solution {
  public:
      string addBinary(string a, string b) {
          string s = "";
  
          int c = 0, i = a.size() - 1, j = b.size() - 1;
          while(i >= 0 || j >= 0 || c == 1)
          {
              c += i >= 0 ? a[i --] - '0' : 0;
              c += j >= 0 ? b[j --] - '0' : 0;
              s = char((c & 1) + '0') + s;
              c >>= 1;
          }
          return s;
      }
  };
  ```