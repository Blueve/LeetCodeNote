Add Binary
==========

## C++

  - Answer

  ```cpp
  class Solution {
	public:
      string addBinary(string a, string b) {
          int lenA(a.size());
          int lenB(b.size());
          int len(lenB), d(abs(lenA - lenB));
          
          if(lenB > lenA)
          {
              string tmp(a);
              a = b; b = tmp;
          }
          
          
          for(int i(a.size() - 1); i >= 0; i--)
          {
              if(i - d >= 0)
                  a[i] += b[i - d] - '0';
              if(a[i] == '2')
              {
                  a[i]      = '0';
                  if(i == 0) a = "1" + a;
                  else       a[i - 1] +=  1 ; 
              }
              else if(a[i] == '3')
              {
                  a[i]      = '1';
                  if(i == 0) a = "1" + a;
                  else       a[i - 1] +=  1 ; 
              }
          }
          
          return a;
      }
  };
  ```