Valid Palindrome
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      bool isPalindrome(string s) {
          int len(s.size());
          for(int i(0), j(len - 1); i < j; )
          {
              auto l = s[i] > 'Z' ? s[i] - ('a' - 'A') : s[i];
              auto r = s[j] > 'Z' ? s[j] - ('a' - 'A') : s[j];
              if(l < '0' || (l > '9' && l < 'A') || l > 'Z'){ ++i; continue; }
              if(r < '0' || (r > '9' && r < 'A') || r > 'Z'){ --j; continue; }
              
              if(l != r) return false;
              ++i, --j;
          }
          return true;
      }
  };
  ```