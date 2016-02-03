Valid Anagram
==========

## C++

  - Answer

  ```cpp
  class Solution {
  public:
      bool isAnagram(string s, string t) {
          int len(s.size());
          if(len != t.size()) return false;
          
          char map[26] = {0};
          for(int i(0); i < len; ++i)
          {
              map[s[i] - 'a']++;
              map[t[i] - 'a']--;
          }
          for(int i(0); i < 26; ++i)
              if(map[i]) return false;
          return true;
      }
  };
  ```